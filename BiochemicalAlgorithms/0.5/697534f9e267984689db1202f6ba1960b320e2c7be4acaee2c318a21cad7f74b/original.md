```
bond_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Bond{T}
```

Returns the `Bond{T}` associated with the given `idx` in `sys`. Throws a `KeyError` if no such bond exists.
