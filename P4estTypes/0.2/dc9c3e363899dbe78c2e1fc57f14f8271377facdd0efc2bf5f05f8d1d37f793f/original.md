```
lnodes(forest::Pxest; ghost = nothing, degree = 1)
```

Construct a parallel node numbering for the `forest`. If the ghost layer `ghost` is not provided it will be constructed.

A `degree > 0` indicates that degree `degree` Lobotto nodes will be constructed.  A `degree < 0` indicates that the boundary objects (faces, edges, and corners) will be numbered.

See `@doc P4estTypes.P4est.p4est_lnodes_t` and `@doc P4estTypes.P4est.p8est_lnodes_t` for a more detailed discussion of the numbering based on `degree`.
