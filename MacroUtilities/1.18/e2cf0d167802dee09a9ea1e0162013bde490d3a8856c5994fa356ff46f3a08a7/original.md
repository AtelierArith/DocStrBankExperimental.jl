```
NamedTupleExpr(names::Vector{Symbol}; kw_head::Bool=false)
```

Returns a `NamedTupleExpr` built from `names`. 

If `kw_head == true`, this expression is of the form `(; names...)`, and otherwise it is of the form `(names...)`
