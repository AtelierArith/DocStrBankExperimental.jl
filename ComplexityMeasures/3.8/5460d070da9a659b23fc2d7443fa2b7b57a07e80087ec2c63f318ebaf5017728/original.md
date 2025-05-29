```
ZhuSingh <: DifferentialInfoEstimator
ZhuSingh(definition = Shannon(); k = 1, w = 0)
```

The `ZhuSingh` estimator [Zhu2015](@cite) computes the [`Shannon`](@ref) differential [`information`](@ref) of a multi-dimensional [`StateSpaceSet`](@ref), with logarithms to the `base` specified in `definition`.

## Description

Assume we have samples $\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ from a continuous random variable $X \in \mathbb{R}^d$ with support $\mathcal{X}$ and density function$f : \mathbb{R}^d \to \mathbb{R}$. `ZhuSingh` estimates the [`Shannon`](@ref) differential entropy

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

Like [`Zhu`](@ref), this estimator approximates probabilities within hyperrectangles surrounding each point `xᵢ ∈ x` using using `k` nearest neighbor searches. However, it also considers the number of neighbors falling on the borders of these hyperrectangles. This estimator is an extension to the entropy estimator in [Singh2003](@citet).

`w` is the Theiler window, which determines if temporal neighbors are excluded during neighbor searches (defaults to `0`, meaning that only the point itself is excluded when searching for neighbours).

See also: [`information`](@ref), [`DifferentialInfoEstimator`](@ref).
