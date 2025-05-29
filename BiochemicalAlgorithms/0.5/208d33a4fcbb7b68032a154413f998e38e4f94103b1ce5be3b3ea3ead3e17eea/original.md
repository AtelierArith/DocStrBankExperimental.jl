```
residue_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Fragment{T}
```

Returns the `Fragment{T}` associated with the given `idx` in `sys`. Throws a `KeyError` if no such fragment exists or if the fragment is not a [`FragmentVariant.Residue`](@ref FragmentVariant).
