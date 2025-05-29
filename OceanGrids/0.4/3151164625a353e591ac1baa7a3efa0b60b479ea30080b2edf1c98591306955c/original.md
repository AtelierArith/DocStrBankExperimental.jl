```
vectorize(x3D, grd)
```

Returns the 1D vector corresponding to the 3D field of `x3D` at the wet boxes of `grd`.

This function essentially returns `x3D[iswet(grd)]` but with some additional checks.
