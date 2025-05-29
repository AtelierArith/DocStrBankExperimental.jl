```
center_of_mass(p::Polyhedron{T}) where {T}
```

Returns the center of mass of `p`, represented as a `Vector{T}` of length `fulldim(p)`. Throws an error if `p` is degenerate.
