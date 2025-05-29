```julia
AdaptiveProbIntsUncertainty(order, save = true)
```

The [ProbInts](https://arxiv.org/abs/1506.04592) method for uncertainty quantification involves the transformation of an ODE into an associated SDE where the noise is related to the timesteps and the order of the algorithm.

`AdaptiveProbIntsUncertainty` is a more automated form of `ProbIntsUncertainty` which uses the error estimate from within adaptive time stepping methods to estimate `σ` at every step.

## Arguments

  * `order` is the order of the ODE solver algorithm.
  * `save` is for choosing whether this callback should control the saving behavior. Generally this is true unless one is stacking callbacks in a `CallbackSet`.

## References

Conrad P., Girolami M., Särkkä S., Stuart A., Zygalakis. K, Probability Measures for Numerical Solutions of Differential Equations, arXiv:1506.04592
