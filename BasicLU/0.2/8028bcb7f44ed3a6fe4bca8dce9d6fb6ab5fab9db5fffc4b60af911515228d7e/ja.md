```
solve!(F::LUFactor, rhs::SparseVector{Float64, Int64}, trans::Char) -> SparseVector{Float64, Int64}
```

スパースな右辺を持つ線形システムを解きます。解は `rhs` を上書きします。`trans` は転置解のために `'T'` である必要があるか、前方解のために `'N'` である必要があります。
