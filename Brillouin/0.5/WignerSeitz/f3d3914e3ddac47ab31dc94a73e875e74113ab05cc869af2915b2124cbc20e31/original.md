```
latticize(c::Cell{D}, basis::AbstractVector{<:AbstractVector{<:Real}})
```

Transform a Wigner-Seitz cell `c` in a Cartesian basis to a lattice basis with (primitive) reciprocal lattice vectors `basis`.

If `c` is not in a Cartesian basis (i.e., if `setting(c) == LATTICE`), `c` is returned as-is.
