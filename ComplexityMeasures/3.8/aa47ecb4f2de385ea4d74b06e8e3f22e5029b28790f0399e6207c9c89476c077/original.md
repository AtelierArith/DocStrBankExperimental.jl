```
KozachenkoLeonenko <: DifferentialInfoEstimator
KozachenkoLeonenko(definition = Shannon(); w::Int = 0)
```

The `KozachenkoLeonenko` estimator [KozachenkoLeonenko1987](@cite) computes the [`Shannon`](@ref) differential [`information`](@ref) of a multi-dimensional [`StateSpaceSet`](@ref), with logarithms to the `base` specified in `definition`.

## Description

Assume we have samples $\{\bf{x}_1, \bf{x}_2, \ldots, \bf{x}_N \}$ from a continuous random variable $X \in \mathbb{R}^d$ with support $\mathcal{X}$ and density function$f : \mathbb{R}^d \to \mathbb{R}$. `KozachenkoLeonenko` estimates the [`Shannon`](@ref) differential entropy

$$
H(X) = \int_{\mathcal{X}} f(x) \log f(x) dx = \mathbb{E}[-\log(f(X))]
$$

using the nearest neighbor method from [KozachenkoLeonenko1987](@citet), as described in [Charzyńska2015](@citet).

`w` is the Theiler window, which determines if temporal neighbors are excluded during neighbor searches (defaults to `0`, meaning that only the point itself is excluded when searching for neighbours).

In contrast to [`Kraskov`](@ref), this estimator uses only the *closest* neighbor.

See also: [`information`](@ref), [`Kraskov`](@ref), [`DifferentialInfoEstimator`](@ref).
