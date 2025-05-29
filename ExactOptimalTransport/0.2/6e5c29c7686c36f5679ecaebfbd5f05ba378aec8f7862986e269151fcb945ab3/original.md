```
ot_plan(::SqEuclidean, μ::Normal, ν::Normal)
```

Compute the optimal transport plan for the Monge-Kantorovich problem with normal distributions `μ` and `ν` as source and target marginals and cost function $c(x, y) = \|x - y\|_2^2$.

See also: [`ot_cost`](@ref), [`emd`](@ref)
