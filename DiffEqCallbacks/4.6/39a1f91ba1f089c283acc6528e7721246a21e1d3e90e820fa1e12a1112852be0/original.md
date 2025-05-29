```julia
ProbIntsUncertainty(σ, order, save = true)
```

The [ProbInts](https://arxiv.org/abs/1506.04592) method for uncertainty quantification involves the transformation of an ODE into an associated SDE where the noise is related to the timesteps and the order of the algorithm.

## Arguments

  * `σ` is the noise scaling factor. It is recommended that `σ` is representative of the size of the errors in a single step of the equation. If such a value is unknown, it can be estimated automatically in adaptive time-stepping algorithms via AdaptiveProbIntsUncertainty
  * `order` is the order of the ODE solver algorithm.
  * `save` is for choosing whether this callback should control the saving behavior. Generally this is true unless one is stacking callbacks in a `CallbackSet`.

## References

Conrad P., Girolami M., Särkkä S., Stuart A., Zygalakis. K, Probability Measures for Numerical Solutions of Differential Equations, arXiv:1506.04592
