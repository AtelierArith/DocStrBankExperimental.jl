```
parent_residue(::Atom)
```

Returns the `Fragment{T}` containing the given atom. Returns `nothing` if no such fragment exists or if the fragment is not a [`FragmentVariant.Residue`](@ref FragmentVariant).
