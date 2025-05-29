```
aislogimpweights(rbm; ...)
```

Computes the logarithmised importance weights for estimating the ratio of the partition functions of the given `rbm` to the RBM with zero weights, but same visible and hidden bias as the `rbm`. This function implements the Annealed Importance Sampling algorithm (AIS) like described in section 4.1.3 of [Salakhutdinov, 2008].

# Optional keyword arguments (for all types of Boltzmann Machines):

  * `ntemperatures`: Number of temperatures for annealing from the starting model to the target model, defaults to 100
  * `temperatures`: Vector of temperatures. By default `ntemperatures` ascending numbers, equally spaced from 0.0 to 1.0
  * `nparticles`: Number of parallel chains and calculated weights, defaults to  100
  * `burnin`: Number of steps to sample for the Gibbs transition between models
