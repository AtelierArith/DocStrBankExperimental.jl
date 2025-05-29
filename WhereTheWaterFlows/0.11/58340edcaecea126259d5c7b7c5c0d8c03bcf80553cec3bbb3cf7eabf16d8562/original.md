```
catchment(dir, ij)
```

Calculates the catchment of one or several grid-point(s) ij.  If desired, the catchment boundary can be calculated with `make_boundaries([c], [1])`.

Input

  * dir – direction field
  * ij – index of the point (2-Tuple, or CartesianIndex) or a Vector{CartesianIndex} for several

Returns

  * catchment – BitArray

Tip: only being off by one grid-point can make the difference      between a tiny and a huge catchment!

See also: `catchments`
