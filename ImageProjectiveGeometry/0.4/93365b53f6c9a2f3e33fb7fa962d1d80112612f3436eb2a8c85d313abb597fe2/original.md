normalise1dpts - Normalises 1D homogeneous points

Function translates and normalises a set of 1D homogeneous points so that their centroid is at the origin and their mean distance from the origin is 1.

```
Usage:   (newpts, T) = normalise1dpts(pts)

Argument:
  pts -  2xN array of 1D homogeneous coordinates

Returns:
  newpts -  2xN array of transformed 1D homogeneous coordinates
  T      -  The 2x2 transformation matrix, newpts = T*pts
```

Note that if one of the points is at infinity no normalisation is possible.  In this case a warning is printed and pts is returned as newpts and T is the identity matrix.

See also: normalise2dpts()
