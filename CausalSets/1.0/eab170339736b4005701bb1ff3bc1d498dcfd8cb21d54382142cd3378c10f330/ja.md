```
estimate_relation_dimension(causet) -> Float64
```

`causet`の次元を、[`count_relations`](@ref)との関係比を計算し、次に$d = 0.01$から$d = 32$まで[`continuous_relation_ratio`](@ref)を二分することで推定します。
