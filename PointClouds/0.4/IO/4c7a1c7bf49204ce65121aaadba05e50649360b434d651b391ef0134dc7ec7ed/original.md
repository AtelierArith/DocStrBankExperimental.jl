```
coordinates(las::LAS, inds = :; crs)
```

Obtain the x-, y-, and z-coordinate of one or multiple point records as a tuple of floating-point numbers. The coordinate reference system (CRS) of the `LAS` is used unless a different `crs` is specified. To obtain coordinates of multiple points, pass a range of indices or `:` (default) as the `index` argument.

# Keywords

  * `crs`: Transform the coordinates to a new coordinate reference system `crs` instead of the current CRS of the `LAS`.

See also: [`LAS`](@ref), [`getcrs`](@ref)
