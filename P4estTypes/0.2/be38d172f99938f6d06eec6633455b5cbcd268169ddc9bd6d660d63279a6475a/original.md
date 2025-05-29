```
iterateforest(forest; kw...)
```

Execute the callbacks passed as keyword arguments for every volume, face, edge, and corner of the rank-local forest.

The keyword arguments (`kw...`) for the iteration are:

  * `ghost = nothing`: the ghost layer associated for the mesh.  Used in `face`, `edge`, and `corner` callbacks for neighboring elements not rank local.
  * `volume = nothing`: Callback used for every volume (aka quadrant) of the local forest with the prototype `volume(forest, ghost, quadrant, quadid, treeid, userdata)`.
  * `face = nothing`: Not implemented yet.
  * `edge = nothing`: Not implemented yet.
  * `corner = nothing`: Not implemented yet.
  * `userdata = nothing`: User data passed to the callbacks.

See `@doc P4estTypes.P4est.p4est_iterate` and `@doc P4estTypes.P4est.p8est_iterate` for more information about the iteration.
