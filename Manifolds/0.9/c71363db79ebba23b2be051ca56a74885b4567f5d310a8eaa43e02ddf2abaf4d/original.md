```
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::CyclicProximalPointEstimation;
    p0=x[1],
    stop_iter=1000000,
    retraction::AbstractRetractionMethod = default_retraction_method(M, eltype(x),),
    inverse_retraction::AbstractInverseRetractionMethod = default_inverse_retraction_method(M, eltype(x),),
    kwargs...,
)
```

Compute the median using [`CyclicProximalPointEstimation`](@extref `ManifoldsBase.CyclicProximalPointEstimation`).

Optionally, provide `p0`, the starting point (by default set to the first data point). `stop_iter` denotes the maximal number of iterations to perform and the `kwargs...` are passed to [`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`) to stop, when the minimal change between two iterates is small. For more stopping criteria check the [`Manopt.jl`](https://manoptjl.org) package and use a solver therefrom.

Optionally, pass `retraction` and `inverse_retraction` method types to specify the (inverse) retraction.

The algorithm is further described in [Bacak:2014](@cite).
