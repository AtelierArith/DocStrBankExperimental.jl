```
SampleEntropy([x]; r = 0.2std(x), kwargs...) <: ComplexityEstimator
```

An estimator for the sample entropy complexity measure [Richman2000](@cite), used with [`complexity`](@ref) and [`complexity_normalized`](@ref).

The keyword argument `r` is mandatory if an input timeseries `x` is not provided.

## Keyword arguments

  * `r::Real`: The radius used when querying for nearest neighbors around points. Its value   should be determined from the input data, for example as some proportion of the   standard deviation of the data.
  * `m::Int = 2`: The embedding dimension.
  * `τ::Int = 1`: The embedding lag.

## Description

An *estimator* for sample entropy using radius `r`, embedding dimension `m`, and embedding lag `τ` is

$$
SampEn(m,r, N) = -\ln{\dfrac{A(r, N)}{B(r, N)}}.
$$

Here,

$$
\begin{aligned}
B(r, m, N) = \sum_{i = 1}^{N-m\tau} \sum_{j = 1, j \neq i}^{N-m\tau} \theta(d({\bf x}_i^m, {\bf x}_j^m) \leq r) \\
A(r, m, N) = \sum_{i = 1}^{N-m\tau} \sum_{j = 1, j \neq i}^{N-m\tau} \theta(d({\bf x}_i^{m+1}, {\bf x}_j^{m+1}) \leq r) \\
\end{aligned},
$$

where $\theta(\cdot)$ returns 1 if the argument is true and 0 otherwise, and $d(x, y)$ computes the Chebyshev distance between $x$ and $y$, and  ${\bf x}_i^{m}$ and ${\bf x}_i^{m+1}$ are `m`-dimensional and `m+1`-dimensional embedding vectors, where `k`-dimensional embedding vectors are constructed from the input timeseries $x(t)$ as

$$
{\bf x}_i^k = (x(i), x(i+τ), x(i+2τ), \ldots, x(i+(k-1)\tau)).
$$

Quoting Richman & Moorman (2002): "SampEn(m,r,N) will be defined except when B = 0, in which case no regularity has been detected, or when A = 0, which corresponds to a conditional probability of 0 and an infinite value of SampEn(m,r,N)". In these cases, `NaN` is returned.

If computing the normalized measure, then the resulting sample entropy is on `[0, 1]`.

!!! note "Flexible embedding lag"
    The original algorithm fixes `τ = 1`. All formulas here are modified to account for any `τ`.


See also: [`entropy_sample`](@ref).
