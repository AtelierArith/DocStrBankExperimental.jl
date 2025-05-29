```
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::WeiszfeldEstimation;
    α = 1.0,
    p0=x[1],
    stop_iter=2000,
    retraction::AbstractRetractionMethod = default_retraction_method(M, eltype(x)),
    inverse_retraction::AbstractInverseRetractionMethod = default_inverse_retraction_method(M, eltype(x)),
    kwargs...,
)
```

Compute the median using [`WeiszfeldEstimation`](@extref `ManifoldsBase.WeiszfeldEstimation`).

Optionally, provide `p0`, the starting point (by default set to the first data point). `stop_iter` denotes the maximal number of iterations to perform and the `kwargs...` are passed to [`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`) to stop, when the minimal change between two iterates is small. For more stopping criteria check the [`Manopt.jl`](https://manoptjl.org) package and use a solver therefrom.

The parameter $α\in (0,2]$ is a step size.

The algorithm is further described in [FletcherVenkatasubramanianJoshi:2008](@cite), especially the update rule in Eq. (6), i.e. Let $q_{k}$ denote the current iterate, $n$ the number of points $x_1,\ldots,x_n$, and

$$
I_k = \bigl\{ i \in \{1,\ldots,n\} \big| x_i \neq q_k \bigr\}
$$

all indices of points that are not equal to the current iterate. Then the update reads $q_{k+1} = \exp_{q_k}(αX)$, where

$$
X = \frac{1}{s}\sum_{i\in I_k} \frac{w_i}{d_{\mathcal M}(q_k,x_i)}\log_{q_k}x_i
\quad
\text{ with }
\quad
s = \sum_{i\in I_k} \frac{w_i}{d_{\mathcal M}(q_k,x_i)},
$$

and where $\mathrm{d}_{\mathcal M}$ denotes the Riemannian [`distance`](@ref).

Optionally, pass `retraction` and `inverse_retraction` method types to specify the (inverse) retraction, which by default use the exponential and logarithmic map, respectively.
