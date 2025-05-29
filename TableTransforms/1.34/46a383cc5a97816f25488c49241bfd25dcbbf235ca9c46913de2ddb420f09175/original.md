```
ProjectionPursuit(; tol=1e-6, maxiter=100, deg=5, perc=0.9, n=100, rng=Random.default_rng())
```

The projection pursuit multivariate transform converts any multivariate distribution into the standard multivariate Gaussian distribution.

This iterative algorithm repeatedly finds a direction of projection `α` that maximizes a score of non-Gaussianity known as the projection index `I(α)`. The samples projected along `α` are then transformed with the [`Quantile`](@ref) transform to remove the non-Gaussian structure. The other coordinates in the rotated orthonormal basis `Q = [α ...]` are left untouched.

The non-singularity of `Q` is controlled by assuring that `norm(det(Q)) ≥ tol`. The iterative  process terminates whenever the transformed samples are "more Gaussian" than `perc`% of `n` randomly generated samples from the standard multivariate Gaussian distribution, or when the  number of iterations reaches a maximum `maxiter`.

# Examples

```julia
ProjectionPursuit()
ProjectionPursuit(deg=10)
ProjectionPursuit(perc=0.85, n=50)
ProjectionPursuit(tol=1e-4, maxiter=250, deg=5, perc=0.95, n=100)

# with rng
using Random
rng = MersenneTwister(2)
ProjectionPursuit(perc=0.85, n=50, rng=rng)
```

See [https://doi.org/10.2307/2289161](https://doi.org/10.2307/2289161) for  further details.
