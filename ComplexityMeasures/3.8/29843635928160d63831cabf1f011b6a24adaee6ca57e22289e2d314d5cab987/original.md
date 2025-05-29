```
Kraskov <: DifferentialInfoEstimator
Kraskov(definition = Shannon(); k::Int = 1, w::Int = 0)
```

The `Kraskov` estimator computes the [`Shannon`](@ref) differential [`information`](@ref) of a multi-dimensional [`StateSpaceSet`](@ref) using the `k`-th nearest neighbor searches method from [Kraskov2004](@citet), with logarithms to the `base` specified in `definition`.

`w` is the Theiler window, which determines if temporal neighbors are excluded during neighbor searches (defaults to `0`, meaning that only the point itself is excluded when searching for neighbours).

## Description

Assume we have samples $\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ from a continuous random variable $X \in \mathbb{R}^d$ with support $\mathcal{X}$ and density function$f : \mathbb{R}^d \to \mathbb{R}$. `Kraskov` estimates the [`Shannon`](@ref) differential entropy

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))].
$$

See also: [`information`](@ref), [`KozachenkoLeonenko`](@ref), [`DifferentialInfoEstimator`](@ref).
