```
transform(p::PointCloud; crs)
```

Transform the coordinates of a `PointCloud` to a new coordinate reference system (CRS). If there is no current CRS, the coordinates remain unchanged but the new CRS is added to the `PointCloud`.

The required keyword argument `crs` can be any string understood by the [PROJ library](https://proj.org/en/9.4/usage/quickstart.html). If set to `nothing`, the CRS is removed.
