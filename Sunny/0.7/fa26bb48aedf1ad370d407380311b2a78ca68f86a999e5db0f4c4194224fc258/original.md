```
q_space_grid(cryst::Crystal, axis1, range1, axis2, range2; offset=[0,0,0], orthogonalize=false)
q_space_grid(cryst::Crystal, axis1, range1, axis2, range2, axis3, range3; orthogonalize=false)
```

Returns a 2D or 3D grid of q-points with uniform spacing. The volume shape is defined by `(axis1, axis2, ...)` in reciprocal lattice units (RLU). Elements of `(range1, range2, ...)` provide coefficients $c_i$ used to define grid positions,

```julia
    offset + c1 * axis1 + c2 * axis2 + ...
```

A nonzero `offset` is allowed only in the 2D case. 

The first range parameter, `range1`, must be a regularly spaced list of coefficients, e.g., `range1 = range(lo1, hi1, n)`. Subsequent range parameters may be a pair of bounds, without grid spacing information. For example, by selecting `range2 = (lo2, hi2)`, an appropriate step-size will be inferred to provide an approximately uniform sampling density in global Cartesian coordinates.

The axes may be non-orthogonal. To extend to an orthohombic volume in global Cartesian coordinates, set `orthogonalize=true`.

For a 1D grid, use [`q_space_path`](@ref) instead.
