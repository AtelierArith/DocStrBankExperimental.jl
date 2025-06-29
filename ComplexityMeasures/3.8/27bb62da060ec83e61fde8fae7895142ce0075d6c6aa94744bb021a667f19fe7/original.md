```
ReverseDispersion <: ComplexityEstimator
ReverseDispersion(; c = 3, m = 2, τ = 1, check_unique = true)
```

Estimator for the reverse dispersion entropy complexity measure [Li2019](@cite).

## Description

[Li2019](@citet) defines the reverse dispersion entropy as

$$
H_{rde} = \sum_{i = 1}^{c^m} \left(p_i - \dfrac{1}{{c^m}} \right)^2 =
\left( \sum_{i=1}^{c^m} p_i^2 \right) - \dfrac{1}{c^{m}}
$$

where the probabilities $p_i$ are obtained precisely as for the [`Dispersion`](@ref) probability estimator. Relative frequencies of dispersion patterns are computed using the given `encoding` scheme , which defaults to encoding using the normal cumulative distribution function (NCDF), as implemented by [`GaussianCDFEncoding`](@ref), using embedding dimension `m` and embedding delay `τ`. Recommended parameter values[Li2018](@cite) are `m ∈ [2, 3]`, `τ = 1` for the embedding, and `c ∈ [3, 4, …, 8]` categories for the Gaussian mapping.

If normalizing, then the reverse dispersion entropy is normalized to `[0, 1]`.

The minimum value of $H_{rde}$ is zero and occurs precisely when the dispersion pattern distribution is flat, which occurs when all $p_i$s are equal to $1/c^m$. Because $H_{rde} \geq 0$, $H_{rde}$ can therefore be said to be a measure of how far the dispersion pattern probability distribution is from white noise.

## Data requirements

The input must have more than one unique element for the default [`GaussianCDFEncoding`](@ref) to be well-defined. [Li2018](@citet) recommends that `x` has at least 1000 data points.

If `check_unique == true` (default), then it is checked that the input has more than one unique value. If `check_unique == false` and the input only has one unique element, then a `InexactError` is thrown when trying to compute probabilities.
