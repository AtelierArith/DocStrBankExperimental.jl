```
cartesian2barycentric_setup(s)
```

Prepare to convert Cartesian to barycentric coordinates.

The returned `setup` structure can be passed to `cartesian2barycentric` instead of the simplex vertices. This pre-calculates certain operations and is more efficient.

# Arguments

  * `s`: Simplex vertices in Cartesian coordinates. `s` has `N=D+1` vertices in `D` dimensions.

# Result

  * `setup`
