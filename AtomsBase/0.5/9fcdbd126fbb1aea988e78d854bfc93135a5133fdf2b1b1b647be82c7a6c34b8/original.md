```
atom_name(species)
atom_name(sys::AbstractSystem, i)
```

Return atomic name (`Symbol`) for `species` or vector of names for `sys`.

Defaults to [`atomic_symbol`](@ref), if `name` field is zero or not defined.
