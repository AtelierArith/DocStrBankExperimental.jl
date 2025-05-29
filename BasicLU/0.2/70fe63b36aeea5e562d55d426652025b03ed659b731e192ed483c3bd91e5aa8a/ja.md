```
x = solve(F::LUFactor, rhs::SparseVector{Float64, Int64}, trans::Char) -> SparseVector{Float64, Int64}
```

スパースな右辺を持つ線形システムを解きます。`rhs` は変更されません。`trans` は転置解のために `'T'` であるか、前方解のために `'N'` でなければなりません。
