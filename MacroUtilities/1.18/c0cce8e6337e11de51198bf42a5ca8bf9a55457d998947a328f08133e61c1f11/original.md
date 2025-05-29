```
name_only(f::FuncArg; is_splat::Bool=f.is_splat) -> FuncArg
```

Returns a new `FuncArg` with the type removed from `f`

If `f.name` is provided, also removes the value field from `f`
