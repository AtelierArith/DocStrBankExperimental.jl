```julia
abstract type PersonParameterAlgorithm
```

An abstract type representing an estimation algorithm for person parameters of an item response model.

Each algorithm must implement the following functions:

  * [`optfun`](@ref): The optimization function passed to the root finding algorithm
  * [`se`](@ref): Calculation of the standard error of estimation.               Defaults to $1/\sqrt{I(\theta)}$, where $I$ is the test information at $\theta$.
