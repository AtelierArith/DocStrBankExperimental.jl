```
C = griddata(A::ClimGrid, londest::AbstractArray{N, 1} where N, latdest::AbstractArray{N, 1} where N)
```

Interpolate `ClimGrid` A onto lat-lon grid defined by londest and latdest vector or array. If an array is provided, it is assumed that the grid is curvilinear (not a regular lon-lat grid) and the user needs to provide the dimension vector ("x" and "y") for such a grid.
