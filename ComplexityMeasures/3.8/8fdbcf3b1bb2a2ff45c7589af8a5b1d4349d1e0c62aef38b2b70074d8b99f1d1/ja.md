```
transferoperator(pts::StateSpaceSet, binning; kw...)
```

矩形分割によって与えられた一連の順序付けられた点の集合に対して、転送演算子を近似します。キーワード `boundary_condition = :none, warn_precise = true` は [`TransferOperator`](@ref) と同様です。
