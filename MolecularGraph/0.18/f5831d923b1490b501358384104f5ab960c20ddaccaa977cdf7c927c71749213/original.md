```
is_aromatic(mol::SimpleMolGraph) -> Vector{Bool}
```

Returns a vector of size $n$ representing whether 1 to $n$th atoms of the given molecule belong to an aromatic ring or not.

See [`is_ring_aromatic`](@ref).
