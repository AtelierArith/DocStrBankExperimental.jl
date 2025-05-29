```
refine!(forest; refine = (_...) -> false, kw...)
```

Refine the quadrants of the forest determined by the `refine` callback. The `refine(forest, treeid, quadrant)` callback is called for each quadrant local to the rank. If the callback returns `true` the `quadrant` will refine into multiple quadrants otherwise it will be untouched.

The other keyword arguments (`kw...`) for the refining are:

  * `recursive`: if `true` refining will be recursive otherwise each rank-local quadrant will only be visited once.
  * `maxlevel = -1`: the maximum level of refinement possible during this call.
  * `init = nothing`: callback function with prototype `init(forest, treeid, quadrant)` called for each quadrant created to initialized the user data.
  * `replace = nothing`: callback function with prototype `replace(forest, treeid, outgoing, incoming)` called for each `outgoing` quadrant with their associated `incoming` quadrants. Note both `outgoing` and `incoming` are arrays with `eltype` [`QuadrantWrapper`](@ref).

See `@doc P4estTypes.P4est.p4est_refine_ext` and `@doc P4estTypes.P4est.p8est_refine_ext` for more information about the underlying p4est refinement functions.
