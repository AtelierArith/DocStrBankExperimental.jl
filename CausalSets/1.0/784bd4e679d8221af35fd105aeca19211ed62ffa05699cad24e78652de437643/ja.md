```
estimate_chain_dimension(causet, k) -> Float64
```

`causet`の次元を、[`count_chains`](@ref)を用いてそのチェーン比を計算し、次に$d = 0.01$から$d = 32$まで[`continuous_chain_ratio`](@ref)を二分法で求めることによって推定します。
