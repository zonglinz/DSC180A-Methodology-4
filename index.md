---
layout: default
title: Quarter 2 Project Ideas
---

# Quarter 2 Project Ideas

**Name:** Zonglin Zhang  
**UCSD email:** [zoz002@ucsd.edu](mailto:zoz002@ucsd.edu)  
**Section:** D09 - Data-driven design of nonlinear architected materials  
**Mentors:** [Igor Sfiligoi (SDSC)](https://shape.ucsd.edu/) and [Nicholas Boechler (MAE)](https://boechler.ucsd.edu/)

## Project Reflection

**What is the most interesting topic covered in your domain this quarter?**

The most interesting topic to me is how spatial variation in nonlinear spring properties can improve impact protection. In our Quarter 1 project, we used a discrete element model (DEM) of a 20-mass spring chain to study how material designs affect the kinetic energy transmitted to the last mass. I found the difference between nominal performance and robustness especially interesting: a design that performs well for one impact can become much less effective after a small change in its coefficients or impact conditions. This made me interested in using machine learning to understand the relationship between design parameters, wave propagation, and reliable impact mitigation. I would like to learn models that help identify designs that perform well across a range of conditions.

**Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

I would like to investigate whether a neural surrogate trained on richer DEM data can predict impact responses and help find robust material designs. Our current dataset already contains 360,000 simulated designs, but its design inputs are limited to at most eight spring coefficients, and the main target is a single kinetic-energy ratio. For Quarter 2, I would like to vary additional physically meaningful inputs, such as impactor mass, impact velocity, and damping, and retain displacement, velocity, or energy time histories from the simulations. I could then compare a neural network with Gaussian-process and tree-based baselines on unseen designs and impact conditions. My main question would be whether the richer data allow a neural model to improve prediction and reduce the number of DEM evaluations needed to identify robust designs. I would first use a small pilot dataset to check simulation and storage costs, then deliver a reproducible comparison of prediction error, design robustness, and simulation budget.

**What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

I would change how we allocate simulations when generating training data. Our Quarter 1 dataset uses uniform rejection sampling, and our separate GP optimization already uses Sobol initialization and adaptive search. I would build on those ideas by comparing random sampling, constrained Sobol sampling, and a hybrid strategy that balances coverage across spring-response regimes before adding samples where a surrogate is uncertain or predicts promising performance. This is relevant because the current dataset contains relatively few bistable springs and very few designs with low transmitted energy. I would keep a separate, fixed test set and compare the sampling strategies under the same simulation budget. I would also group related designs and their perturbed copies within the same data split to avoid overly optimistic evaluation.

**What other techniques would you be interested in using in your project?**

I am interested in active learning, uncertainty estimation, and models that use the structure of the simulated system. I would start with a multilayer perceptron and a small ensemble to explore whether model disagreement helps select useful new simulations. If the dataset includes time-dependent responses, I would also like to investigate a temporal model for predicting selected response histories. As a possible extension, a graph neural network could represent masses as nodes and springs as edges, particularly if we vary the chain length or connectivity. I would compare these methods with simpler baselines and check their performance under coefficient and impact perturbations. My goal is to make the project more focused on machine learning while testing when the additional model complexity is useful.
