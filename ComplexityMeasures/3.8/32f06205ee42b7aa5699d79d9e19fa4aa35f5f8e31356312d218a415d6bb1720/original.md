```
Zhu <: DifferentialInfoEstimator
Zhu(; definition = Shannon(), k = 1, w = 0)
```

The `Zhu` estimator [Zhu2015](@cite) is an extension to [`KozachenkoLeonenko`](@ref), and computes the [`Shannon`](@ref) differential [`information`](@ref) of a multi-dimensional [`StateSpaceSet`](@ref), with logarithms to the `base` specified in `definition`.

## Description

Assume we have samples $\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ from a continuous random variable $X \in \mathbb{R}^d$ with support $\mathcal{X}$ and density function$f : \mathbb{R}^d \to \mathbb{R}$. `Zhu` estimates the [`Shannon`](@ref) differential entropy

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))]
$$

by approximating densities within hyperrectangles surrounding each point `xᵢ ∈ x` using using `k` nearest neighbor searches. `w` is the Theiler window, which determines if temporal neighbors are excluded during neighbor searches (defaults to `0`, meaning that only the point itself is excluded when searching for neighbours).

See also: [`information`](@ref), [`KozachenkoLeonenko`](@ref), [`DifferentialInfoEstimator`](@ref).
