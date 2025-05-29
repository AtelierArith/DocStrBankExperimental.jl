```
basis(x::Union{KPath, KPathInterpolant, Cell})
```

Return the (reciprocal or direct) lattice basis associated with `x`, in Cartesian coordinates.

Methods in Brillouin by default return points in the lattice basis, i.e., points are  referred to `basis(x)`. This corresponds to the `setting(x) == LATTICE`. Coordinates may instead be referred to a Cartesian basis, corresponding to `setting(x) == CARTESIAN` by using [`cartesianize`](@ref). The result of  `basis(x)`, however, is invariant to this and always refers to the lattice basis in Cartesian coordinates.
