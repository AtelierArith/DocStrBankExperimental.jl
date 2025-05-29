```
latticize(kpi::KPathInterpolant{D}, basis::AbstractVector{<:AbstractVector{<:Real}})
```

Transform an interpolated **k**-path `kpi` in a Cartesian basis to a lattice basis with (primitive) reciprocal lattice vectors `basis`.

If `kpi` is not in a Cartesian basis (i.e., if `setting(kpi) == LATTICE`), `kpi` is returned as-is.
