```
estimated(labels::Vector{<:Label}, samples::Matrix{Float64})
```

サンプル（「測定」）のセットに基づいて UncertainValues を推定します。期待値から平均値と共分散行列を計算します。サンプルの各行 `r` は、`labels[r]` によって特定される測定された量を表します。各列は、すべてのラベル付き量の単一の測定セットを表します。
