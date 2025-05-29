```
estimate_relation_dimension(causet) -> Float64
```

Estimate the dimension of `causet` by calculating its relation ratio with [`count_relations`](@ref) and then bisecting [`continuous_relation_ratio`](@ref) from $d = 0.01$ to $d = 32$.
