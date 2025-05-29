```
ApproximateEntropy <: ComplexityEstimator
ApproximateEntropy([x]; r = 0.2std(x), kwargs...)
```

An estimator for the approximate entropy [Pincus1991](@cite) complexity measure, used with [`complexity`](@ref).

The keyword argument `r` is mandatory if an input timeseries `x` is not provided.

## Keyword arguments

  * `r::Real`: The radius used when querying for nearest neighbors around points. Its value   should be determined from the input data, for example as some proportion of the   standard deviation of the data.
  * `m::Int = 2`: The embedding dimension.
  * `τ::Int = 1`: The embedding lag.
  * `base::Real = MathConstants.e`: The base to use for the logarithm. Pincus (1991) uses the   natural logarithm.

## Description

Approximate entropy (ApEn) is defined as

$$
ApEn(m ,r) = \lim_{N \to \infty} \left[ \phi(x, m, r) - \phi(x, m + 1, r) \right].
$$

Approximate entropy is estimated for a timeseries `x`, by first embedding `x` using embedding dimension `m` and embedding lag `τ`, then searching for similar vectors within tolerance radius `r`, using the estimator described below, with logarithms to the given `base` (natural logarithm is used in Pincus, 1991).

Specifically, for a finite-length timeseries `x`, an estimator for $ApEn(m ,r)$ is

$$
ApEn(m, r, N) = \phi(x, m, r, N) -  \phi(x, m + 1, r, N),
$$

where `N = length(x)` and

$$
\phi(x, k, r, N) =
\dfrac{1}{N-(k-1)\tau} \sum_{i=1}^{N - (k-1)\tau}
\log{\left(
    \sum_{j = 1}^{N-(k-1)\tau} \dfrac{\theta(d({\bf x}_i^m, {\bf x}_j^m) \leq r)}{N-(k-1)\tau}
    \right)}.
$$

Here, $\theta(\cdot)$ returns 1 if the argument is true and 0 otherwise,  $d({\bf x}_i, {\bf x}_j)$ returns the Chebyshev distance between vectors  ${\bf x}_i$ and ${\bf x}_j$, and the `k`-dimensional embedding vectors are constructed from the input timeseries $x(t)$ as

$$
{\bf x}_i^k = (x(i), x(i+τ), x(i+2τ), \ldots, x(i+(k-1)\tau)).
$$

!!! note "Flexible embedding lag"
    In the original paper, they fix `τ = 1`. In our implementation, the normalization constant is modified to account for embeddings with `τ != 1`.

