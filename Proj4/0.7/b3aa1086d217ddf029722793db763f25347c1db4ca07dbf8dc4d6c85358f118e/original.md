```
transform!(src_projection, dest_projection, position [, radians=false])
```

Transform between geographic or projected coordinate systems, modifying `position` in place.

Args:

```
src      - Source coordinate system definition
dest     - Destination coordinate system definition
position - An array of coordinates to be transformed in place.  If `position` is a
           Vector of length 2 or 3 it's treated as a single point.  For
           geographic coordinate systems, the first two columns are the
           *longitude* and *latitude*, in that order.  To transform an
           array of points, a matrix of shape Nx2 or Nx3 may be used.
radians  - If true, treat geographic lon,lat coordinates as radians on
           input and output.
```

Returns:

```
position - Transformed position
```
