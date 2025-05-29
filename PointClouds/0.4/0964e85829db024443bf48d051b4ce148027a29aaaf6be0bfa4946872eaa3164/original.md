```
PointCloud(input; kws...)
```

Load (a subset of) point data into memory for processing. The data is stored in “columnar format”, where each point attribute (coordinates, intensity, etc.) forms a column with one entry (row) per point. Attributes can be added/updated/removed in further processing steps.

The `input` can be one or multiple (passed as tuple/array) [`LAS`](@ref) values, or values that can be passed to [`read(input, LAS)`](@ref Base.read(::IO, ::LAS)) such as the path to a LAS/LAZ file. Alternatively, a `NamedTuple` of `Vector`s can be passed, where the `x`, `y`, and `z`-names are interpreted as coordinates and all the other names as additional attributes.

# Keywords

  * `attributes`: Additional attributes that are included for each point. Attributes are specified as a tuple/array of functions that are applied to each point to compute the attribute. By default, the name of the function is used as attribute name, but a manual name can be specified by passing a `Pair{Symbol,Function}` instead. The attributes can also be defined with a `NamedTuple`, where the keys are the attribute names and the values are the functions. Default: `()`.
  * `coordinates`: Subset of coordinates to load, e.g. `(:x, :y)` if the vertical coordinates are not required. Default: `(:x, :y, :z)`.
  * `crs`: Coordinate reference system (CRS) that the x/y/z-coordinates should be transformed to, specified as any string understood by the [PROJ library](https://proj.org/en/9.4/usage/quickstart.html). Default: CRS of the first input.
  * `extent`: Only include points that lie within a limited range of coordinates, specified as a tuple with the lower and upper bounds. Each bound is a tuple of x- and y-values, e.g. `extent = ((0, 0), (1, 2))` for $0 ≤ x ≤ 1$ and $0 ≤ y ≤ 2$.
  * `filter`: Predicate function that is called on each point to exclude points for which the `filter` function returns `false`.

# Examples

```
PointCloud(las; attributes = (intensity, :t => gps_time))
PointCloud(las; attributes = (i = intensity, t = gps_time))
PointCloud(las; crs = "EPSG:4326", extent = ((-73.97, 40.80), (-73.95, 40.82)))
```
