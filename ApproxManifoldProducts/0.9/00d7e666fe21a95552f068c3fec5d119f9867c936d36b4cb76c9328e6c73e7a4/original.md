```julia
makePointFromCoords(M, coords)
makePointFromCoords(M, coords, u0)
makePointFromCoords(M, coords, u0, ϵ)
makePointFromCoords(M, coords, u0, ϵ, retraction_method)

```

Helper function to convert coordinates to a desired on-manifold point.

DevNotes

  * FIXME need much better consolidation or even removal of this function entirely.

      * This function makes too strong an assumption of groups

Notes

  * `u0` is used to identify the data type for a point
  * Pass in a different `exp` if needed.
