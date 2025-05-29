```
atom_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Atom{T}
```

Returns the `Atom{T}` associated with the given `idx` in `sys`. Throws a `KeyError` if no such atom exists.
