```
parent_nucleotide(::Atom)
```

Returns the `Fragment{T}` containing the given atom. Returns `nothing` if no such fragment exists or if the fragment is not a [`FragmentVariant.Nucleotide`](@ref FragmentVariant).
