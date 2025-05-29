```
LatitudeLongitudeGrid(rectilinear_grid::RectilinearGrid; radius=R_Earth, origin=(0, 0))
```

Construct a `LatitudeLongitudeGrid` from a `RectilinearGrid`. The horizontal coordinates of the rectilinear grid are transformed to longitude-latitude coordinates in degrees, accounting for spherical Earth geometry. The longitudes are computed approximately using the latitudinal origin.

The vertical coordinate and architecture are inherited from the input grid.

# Keyword Arguments

  * `radius`: The radius of the sphere, defaults to Earth's mean radius (≈ 6371 km)
  * `origin`: Tuple of (longitude, latitude) in degrees specifying the origin of the rectilinear grid
