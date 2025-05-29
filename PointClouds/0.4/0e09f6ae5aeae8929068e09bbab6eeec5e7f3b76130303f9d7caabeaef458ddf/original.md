```
rasterize(p::PointCloud, dims; kws...)
```

Rasterize points in a `PointCloud` by assigning them to gridded locations within a target area. The raster has dimensions `dims` (given as a tuple of integers), is aligned with the axes of the x-/y-coordinates, and spans the full bounding box of the points, unless the extent is narrowed with keyword arguments. By default, each raster location is mapped to the points that lie within its “pixel area”, unless the `radius` or `neighbors` keyword arguments are specified. Currently, only 2D rasterization is supported.

Note that with the default “pixel area” method, each point gets assigned to exactly one raster location if it lies within the bounds of the raster. With the `radius` and `neighbors` methods, points may get assigned to multiple or zero raster locations. Furthermore, only the `neighbors` method guarantees that each raster location has points assigned to it; the other methods may produce empty pixels.

# Keywords

  * `extent`: Specify the extent of the raster area as a tuple with the lower and upper bounds of the coordinates. Each entry is a tuple of x- and y-values, e.g. `extent = ((0, 0), (1, 2))` for $0 ≤ x ≤ 1$ and $0 ≤ y ≤ 2$.
  * `radius`: Assign all points within a distance of `radius` from the pixel center to that raster location. The unit of `radius` is the same as the x-/y-coordinates. Note that points may get assigned to multiple or zero raster locations.
  * `neighbors`: Assign a specific number `neighbors` of points to each raster location based on which ones are closest to the pixel center.
