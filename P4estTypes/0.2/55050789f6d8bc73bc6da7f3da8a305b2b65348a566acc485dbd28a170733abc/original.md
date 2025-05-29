```
balance!(forest; kw...)
```

Enforce the two-to-one quadrant size constraint across the forest.  By default, this constraint is enforced across faces, edges, and corners.

The keyword arguments (`kw...`) for the balancing are:

  * `connect`: type of constraint enforced which can take the values:

      * `P4estTypes.CONNECT_FULL(Val(4))`: enforce across face, and corner.
      * `P4estTypes.CONNECT_FULL(Val(8))`: enforce across face, edge, and corner.
      * `P4estTypes.CONNECT_FACE(Val(4))`: enforce across face.
      * `P4estTypes.CONNECT_FACE(Val(8))`: enforce across face.
      * `P4estTypes.CONNECT_EDGE(Val(8))`: enforce across face and edge.
      * `P4estTypes.CONNECT_CORNER(Val(4))`: enforce across face and corner.
      * `P4estTypes.CONNECT_CORNER(Val(8))`: enforce across face, edge, and corner.
  * `init = nothing`: callback function with prototype `init(forest, treeid, quadrant)` called for each quadrant created to initialized the user data.
  * `replace = nothing`: callback function with prototype `replace(forest, treeid, outgoing, incoming)` called for each `outgoing` quadrant with their associated `incoming` quadrants. Note both `outgoing` and `incoming` are arrays with `eltype` [`QuadrantWrapper`](@ref).

See `@doc P4estTypes.P4est.p4est_balance_ext` and `@doc P4estTypes.P4est.p8est_balance_ext` for more information about the underlying p4est balance functions.
