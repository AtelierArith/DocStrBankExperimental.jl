```
MixtureDistribution(components, weights)
```

A custom mixture distribution implementation, parameterized by:

  * `C` type family of the mixture
  * `CT` the type for the weights

This implementation solves:

  * [Distributions.jl Issue 1669](https://github.com/JuliaStats/Distributions.jl/issues/1669)
  * [ReactiveMP.jl Issue 253](https://github.com/reactivebayes/ReactiveMP.jl/issues/253)
