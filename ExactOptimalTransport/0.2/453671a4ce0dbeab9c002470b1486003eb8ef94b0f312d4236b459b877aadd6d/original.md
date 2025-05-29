```
ot_cost(
    c, μ::ContinuousUnivariateDistribution, ν::UnivariateDistribution; plan=nothing
)
```

Compute the optimal transport cost for the Monge-Kantorovich problem with univariate distributions `μ` and `ν` as source and target marginals and cost function `c` of the form $c(x, y) = h(|x - y|)$ where $h$ is a convex function.

In this setting, the optimal transport cost can be computed as

$$
\int_0^1 c(F_\mu^{-1}(x), F_\nu^{-1}(x)) \mathrm{d}x
$$

where $F_\mu^{-1}$ and $F_\nu^{-1}$ are the quantile functions of `μ` and `ν`, respectively.

A pre-computed optimal transport `plan` may be provided.

See also: [`ot_plan`](@ref), [`emd2`](@ref)
