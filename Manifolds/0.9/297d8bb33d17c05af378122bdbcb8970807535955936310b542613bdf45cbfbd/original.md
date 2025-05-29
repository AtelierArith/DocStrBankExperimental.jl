```
mean(M::AbstractManifold, x::AbstractVector[, w::AbstractWeights]; kwargs...)
```

Compute the (optionally weighted) Riemannian center of mass also known as Karcher mean of the vector `x` of points on the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)  `M`, defined as the point that satisfies the minimizer

$$
\operatorname{argmin}_{y ∈ \mathcal M} \frac{1}{2 \sum_{i=1}^n w_i} \sum_{i=1}^n w_i\mathrm{d}_{\mathcal M}^2(y,x_i),
$$

where $\mathrm{d}_{\mathcal M}$ denotes the Riemannian [`distance`](@ref).

In the general case, the [`GradientDescentEstimation`](@extref `ManifoldsBase.GradientDescentEstimation`) is used to compute the mean.     mean(         M::AbstractManifold,         x::AbstractVector,         [w::AbstractWeights,]         method::AbstractApproximationMethod=default*approximation*method(M, mean);         kwargs...,     )

Compute the mean using the specified `method`.

```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::GradientDescentEstimation;
    p0=x[1],
    stop_iter=100,
    retraction::AbstractRetractionMethod = default_retraction_method(M),
    inverse_retraction::AbstractInverseRetractionMethod = default_retraction_method(M, eltype(x)),
    kwargs...,
)
```

Compute the mean using the gradient descent scheme [`GradientDescentEstimation`](@extref `ManifoldsBase.GradientDescentEstimation`).

Optionally, provide `p0`, the starting point (by default set to the first data point). `stop_iter` denotes the maximal number of iterations to perform and the `kwargs...` are passed to [`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`) to stop, when the minimal change between two iterates is small. For more stopping criteria check the [`Manopt.jl`](https://manoptjl.org) package and use a solver therefrom.

Optionally, pass `retraction` and `inverse_retraction` method types to specify the (inverse) retraction.

The Theory stems from [Karcher:1977](@cite) and is also described in [PennecArsigny:2012](@cite) as the exponential barycenter. The algorithm is further described in[AfsariTronVidal:2013](@cite).
