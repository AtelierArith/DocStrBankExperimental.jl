```
latticize(kp::KPath{D}, basis::AbstractVector{<:AbstractVector{<:Real}})
```

Transform a **k**-path `kp` in a Cartesian basis to a lattice basis with (primitive) reciprocal lattice vectors `basis`.

If `kp` is not in a Cartesian basis (i.e., if `setting(kp) == LATTICE`), `kp` is returned as-is.
