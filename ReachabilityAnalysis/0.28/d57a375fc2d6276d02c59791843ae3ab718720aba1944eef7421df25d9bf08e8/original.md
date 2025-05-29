```
project(R::AbstractLazyReachSet, variables::NTuple{D,Int};
        check_vars::Bool=true) where {D}
```

Projects a reach-set onto the subspace spanned by the given variables.

### Input

  * `R`          – reach-set
  * `vars`       – tuple of variables for the projection
  * `check_vars` – (optional, default: `true`) if `true`, check that the given variable                 indices `vars` are a subset of the variables of `R`

### Output

A `SparseReachSet` whose variable indices are given by `vars`.

The type of the new reach-set depends on the type of the reach-set `R`:

  * If `R` contains a hyperrectangular set, the output is a hyperrectangle.
  * If `R` contains a zonotopic set, the output is a zonotope.
  * Otherwise, the return type is a polytope either in constraint representation or in vertex representation, depending on the dimension and the properties of `M`. For details, see `LazySets.project`.

### Notes

This function can be used to project a reach-set onto a lower-dimensional sub-space. The projection is concrete, and it consists of mapping the reach-set `X = set(R)` to a new reach-set through to `MX`, where `M` is the projection matrix associated with the given variables `vars`.

To project onto the time variable, use the index `0`. For instance, `(0, 1)` projects onto the time variable and the first variable in `R`.
