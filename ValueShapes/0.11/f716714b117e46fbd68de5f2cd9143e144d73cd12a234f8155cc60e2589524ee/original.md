```
ReshapedDist <: Distribution
```

An multivariate distribution reshaped using a given [`AbstractValueShape`](@ref).

Constructors:

```julia
    ReshapedDist(dist::MultivariateDistribution, shape::AbstractValueShape)
```

In addition, `MultivariateDistribution`s can be reshaped via

```julia
(shape::AbstractValueShape)(dist::MultivariateDistribution)
```

with the difference that

```julia
(shape::ArrayShape{T,1})(dist::MultivariateDistribution)
```

will return the original `dist` instead of a `ReshapedDist`.
