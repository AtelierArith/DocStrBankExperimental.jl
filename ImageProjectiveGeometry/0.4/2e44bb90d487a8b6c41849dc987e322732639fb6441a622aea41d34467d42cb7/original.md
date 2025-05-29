normalise2dpts - Normalises 2D homogeneous points

```
Usage:   (newpts, T) = normalise2dpts(pts)

Argument:
     pts -  3xN array of 2D homogeneous coordinates.

Returns:
  newpts -  3xN array of transformed 2D homogeneous coordinates.  The
            scaling parameter is normalised to 1 unless the point is at
            infinity.
  T      -  The 3x3 transformation matrix, newpts = T*pts.
```

Function translates and normalises a set of 2D homogeneous points so that their centroid is at the origin and their mean distance from the origin is sqrt(2).  This process typically improves the conditioning of any equations used to solve homographies, fundamental matrices etc.

If there are some points at infinity the normalisation transform is calculated using just the finite points.  Being a scaling and translating transform this will not affect the points at infinity.
