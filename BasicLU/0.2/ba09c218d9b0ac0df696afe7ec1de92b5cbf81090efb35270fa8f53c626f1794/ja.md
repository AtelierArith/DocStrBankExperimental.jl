```
solve!(F::LUFactor, rhs::Vector{Float64}, trans::Char) -> Vector{Float64}
```

密な右辺を持つ線形システムを解きます。解は `rhs` を上書きします。`trans` は転置解のために `'T'`、または前方解のために `'N'` でなければなりません。
