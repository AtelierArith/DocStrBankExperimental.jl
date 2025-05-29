```
NamedTupleExpr(names::Vector{Symbol}; kw_head::Bool=false)
```

`names` から構築された `NamedTupleExpr` を返します。

`kw_head == true` の場合、この式は `(; names...)` の形になり、それ以外の場合は `(names...)` の形になります。
