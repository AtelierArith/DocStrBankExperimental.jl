```
Gao <: DifferentialInfoEstimator
Gao(definition = Shannon(); k = 1, w = 0, corrected = true)
```

The `Gao` estimator [Gao2015](@cite) computes the [`Shannon`](@ref) differential [`information`](@ref), using a `k`-th nearest-neighbor approach based on [Singh2003](@citet), with logarithms to the `base` specified in `definition`.

`w` is the Theiler window, which determines if temporal neighbors are excluded during neighbor searches (defaults to `0`, meaning that only the point itself is excluded when searching for neighbours).

[Gao2015](@citet) give two variants of this estimator. If `corrected == false`, then the uncorrected version is used. If `corrected == true`, then the corrected version is used, which ensures that the estimator is asymptotically unbiased.

## Description

Assume we have samples $\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ from a continuous random variable $X \in \mathbb{R}^d$ with support $\mathcal{X}$ and density function$f : \mathbb{R}^d \to \mathbb{R}$. `KozachenkoLeonenko` estimates the [`Shannon`](@ref) differential entropy

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$
