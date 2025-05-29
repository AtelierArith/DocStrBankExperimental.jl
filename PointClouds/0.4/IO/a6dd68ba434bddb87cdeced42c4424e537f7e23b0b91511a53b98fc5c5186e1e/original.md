```
coordinates(Function, las::LAS; crs)
```

Create a function that takes a `PointRecord` as its argument and returns the rescaled coordinates of that point; in the coordinate reference system (CRS) of `las` unless a different `crs` is specified.

See also: [`LAS`](@ref), [`getcrs`](@ref)
