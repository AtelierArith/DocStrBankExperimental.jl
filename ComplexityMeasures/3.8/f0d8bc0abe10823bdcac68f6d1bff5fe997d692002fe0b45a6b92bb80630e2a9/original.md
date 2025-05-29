```
GeneralizedSchuermann <: DiscreteInfoEstimatorShannon
GeneralizedSchuermann(definition = Shannon(); a = 1.0)
```

The `GeneralizedSchuermann` estimator is used with [`information`](@ref) to compute the discrete [`Shannon`](@ref) entropy with the bias-corrected estimator given in [Grassberger2022](@citet).

The "generalized" part of the name, as opposed to the [Schurmann2004](@citet) estimator ([`Schuermann`](@ref)), is due to the possibility of picking difference parameters $a_i$ for different outcomes. If different parameters are assigned to the different outcomes, `a` must be a vector of parameters of length `length(outcomes)`, where the outcomes are obtained using [`outcomes`](@ref). See [Grassberger2022](@citet) for more information. If `a` is a real number, then $a_i = a \forall i$, and the estimator reduces to the [`Schuermann`](@ref) estimator.

## Description

For a set of $N$ observations over $M$ outcomes, the estimator is given by

$$
H_S^{opt} = \varphi(N) - \dfrac{1}{N} \sum_{i=1}^M n_i G_{n_i}(a_i),
$$

where $n_i$ is the observed frequency of the i-th outcome,

$$
G_n(a) = \varphi(n) + (-1)^n \int_0^a \dfrac{x^{n - 1}}{x + 1} dx,
$$

$G_n(1) = G_n$ and $G_n(0) = \varphi(n)$, and

$$
G_n = \varphi(n) + (-1)^n \int_0^1 \dfrac{x^{n - 1}}{x + 1} dx.
$$
