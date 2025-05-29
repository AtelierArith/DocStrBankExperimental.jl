```
setting(x::Union{KPath, KPathInterpolant, Cell})
```

Return the basis setting of coordinates in `x`. The returned value is a member of the [`BasisEnum`](@ref) enum with member values `LATTICE` (i.e. coordinates in the basis of the lattice vectors) or `CARTESIAN` (i.e. coordinates in the Cartesian basis). By default, methods in Brillouin return coordinates in the `LATTICE` setting.
