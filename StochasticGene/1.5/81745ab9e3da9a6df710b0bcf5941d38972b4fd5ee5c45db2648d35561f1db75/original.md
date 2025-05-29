```
module StochasticGene
```

A Julia module for simulation and Bayesian inference of parameters of stochastic models of gene transcription.

# Overview

This module provides a comprehensive set of tools for simulating stochastic models of gene transcription and performing Bayesian inference on model parameters. It includes functions for:

  * Transition rate calculations
  * Metropolis Hastings MCMC for computing posterior distributions
  * Input/output operations
  * Chemical master equation solutions for likelihood functions
  * Commonly used utility functions
  * Probability distributions via direct simulation using Gillespie and Gibson-Bruck algorithms
  * Model fitting to data
  * Post-fit analysis and plotting
  * Functions for use on the NIH cluster Biowulf
  * Hidden Markov models

# - GPU-accelerated computations using CUDA (optional)

# Included Files

  * `transition_rate_make.jl`: Functions for transition rate calculations.
  * `metropolis_hastings.jl`: Metropolis Hastings MCMC for computing posterior distributions of model parameters.
  * `io.jl`: Input/output functions.
  * `chemical_master.jl`: Chemical master equation solutions of stochastic models for likelihood functions in fitting algorithms.
  * `utilities.jl`: Commonly used utility functions.
  * `simulator_coupled.jl`: Probability distributions by direct simulation of stochastic models using Gillespie and Gibson-Bruck algorithms.
  * `fit.jl`: Functions for fitting models to data.
  * `analysis.jl`: Functions for post-fit analysis and plots.
  * `biowulf.jl`: Functions for use on NIH cluster Biowulf.
  * `hmm.jl`: Functions for hidden Markov models.
