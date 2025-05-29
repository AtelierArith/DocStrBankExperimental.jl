```
vec(d::Distribution{<:ArrayLikeVariate})
```

Return a [`MultivariateDistribution`](@ref) of `vec(X)` where `X` is a random variable with distribution `d`.

The default implementation returns a [`ReshapedDistribution`](@ref). However, it can return more optimized distributions for specific types of distributions and numbers of dimensions. Therefore it is recommended to use `vec` instead of the constructor of `ReshapedDistribution`.

# Implementation

Since `vec(d)` is defined as `reshape(d, length(d))` one should implement `reshape(d, ::Tuple{Int})` rather than `vec`.

See also: [`reshape`](@ref)
