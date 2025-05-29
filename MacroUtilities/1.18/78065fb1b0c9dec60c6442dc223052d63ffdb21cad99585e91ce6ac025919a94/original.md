```
NamedTupleArg(; key::Symbol, value=not_provided, is_splat::Bool=false, kw_head::Bool)

NamedTupleArg(key::Symbol; kw_head::Bool)
```

Matches a `key = value` or a `key` argument inside a `NamedTuple` expression

If `kw_head == true`, the expression head is set to `:kw`, otherwise `:(=)`
