```
x = solve(F::LUFactor, rhs::Vector{Float64}, trans::Char) -> Vector{Float64}
```

密な右辺を持つ線形システムを解きます。`rhs` は変更されません。`trans` は転置解のために `'T'` である必要があるか、前方解のために `'N'` である必要があります。
