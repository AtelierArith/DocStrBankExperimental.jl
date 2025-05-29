```
coordinates(p::PointCloud, index; crs)
```

Obtain the x-, y-, and z-coordinate of the `index`-th point as a tuple of `Float64`s. The coordinate reference system (CRS) of the `PointCloud` is used unless a different crs is specified. To obtain coordinates of multiple points, pass a range of indices or `:` as the `index` argument.

Provide the `crs` keyword argument to transform the coordinates to a new CRS instead of the current CRS of the `PointCloud`.
