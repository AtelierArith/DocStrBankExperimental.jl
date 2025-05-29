```
chain_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Chain{T}
```

Returns the `Chain{T}` associated with the given `idx` in `sys`. Throws a `KeyError` if no such chain exists.
