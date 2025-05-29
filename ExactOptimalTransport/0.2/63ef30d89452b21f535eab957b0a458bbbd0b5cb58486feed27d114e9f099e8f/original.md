```
ot_plan(c, μ::DiscreteNonParametric, ν::DiscreteNonParametric)
```

Compute the optimal transport cost for the Monge-Kantorovich problem with univariate discrete distributions `μ` and `ν` as source and target marginals and cost function `c` of the form $c(x, y) = h(|x - y|)$ where $h$ is a convex function.

In this setting, the optimal transport plan can be computed analytically. It is returned as a sparse matrix.

See also: [`ot_cost`](@ref), [`emd`](@ref)
