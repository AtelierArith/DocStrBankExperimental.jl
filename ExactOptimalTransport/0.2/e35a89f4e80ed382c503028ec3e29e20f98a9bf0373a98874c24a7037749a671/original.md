```
ot_cost(
    c, μ::DiscreteNonParametric, ν::DiscreteNonParametric; plan=nothing
)
```

Compute the optimal transport cost for the Monge-Kantorovich problem with discrete univariate distributions `μ` and `ν` as source and target marginals and cost function `c` of the form $c(x, y) = h(|x - y|)$ where $h$ is a convex function.

In this setting, the optimal transport cost can be computed analytically.

A pre-computed optimal transport `plan` may be provided.

See also: [`ot_plan`](@ref), [`emd2`](@ref)
