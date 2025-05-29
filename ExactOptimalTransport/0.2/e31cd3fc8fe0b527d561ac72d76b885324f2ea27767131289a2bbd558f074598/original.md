```
ot_plan(c, μ::ContinuousUnivariateDistribution, ν::UnivariateDistribution)
```

Compute the optimal transport plan for the Monge-Kantorovich problem with univariate distributions `μ` and `ν` as source and target marginals and cost function `c` of the form $c(x, y) = h(|x - y|)$ where $h$ is a convex function.

In this setting, the optimal transport plan is the Monge map

$$
T = F_\nu^{-1} \circ F_\mu
$$

where $F_\mu$ is the cumulative distribution function of `μ` and $F_\nu^{-1}$ is the quantile function of `ν`.

See also: [`ot_cost`](@ref), [`emd`](@ref)
