```
estimate_chain_dimension(causet, k) -> Float64
```

Estimate the dimension of `causet` by calculating its chain ratio with [`count_chains`](@ref) and then bisecting [`continuous_chain_ratio`](@ref) from $d = 0.01$ to $d = 32$.
