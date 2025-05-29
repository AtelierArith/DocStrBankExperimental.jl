```
SurfaceNormal(ndimensions::FInt)
```

Construct surface normal evaluator when the default calculation of the normal vector based on the columns of the Jacobian matrix should be used. 

The normal vector has `ndimensions` entries.

When the columns of the `tangents` array are parallel (or one of them is a zero vector), the normal cannot be normalized to unit length (it is a zero vector). In that case a zero vector is returned, and a warning is printed.
