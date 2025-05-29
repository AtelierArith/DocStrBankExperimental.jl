```
coarsen!(forest; coarsen = (_...) -> false, kw...)
```

Coarsen the quadrants of the forest determined by the `coarsen` callback. The `coarsen(forest, treeid, siblings)` callback is called for each set of sibling quadrants local to the rank that are eligible for coarsening. If the callback returns `true` the `siblings` will coarsen into one quadrant otherwise they will be untouched.

The other keyword arguments (`kw...`) for the coarsening are:

  * `recursive = false`: if `true` coarsening will be recursive otherwise each set of rank-local siblings will only be visited once.
  * `init = nothing`: callback function with prototype `init(forest, treeid, quadrant)` called for each quadrant created to initialized the user data.
  * `replace = nothing`: callback function with prototype `replace(forest, treeid, outgoing, incoming)` called for each set of `outgoing` quadrants with their associated `incoming` quadrant.  Note  both `outgoing` and `incoming` are arrays with `eltype`  [`QuadrantWrapper`](@ref).

See `@doc P4estTypes.P4est.p4est_coarsen_ext` and `@doc P4estTypes.P4est.p8est_coarsen_ext` for more information about the underlying p4est coarsening functions.
