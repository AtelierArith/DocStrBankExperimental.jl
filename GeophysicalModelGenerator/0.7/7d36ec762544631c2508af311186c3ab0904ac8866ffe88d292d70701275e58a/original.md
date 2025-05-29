```
Grid_counts = point_to_nearest_grid(Point::GeoData, Grid::GeoData; radius_factor=1)
```

Uses nearest neighbour interpolation to count how many points (given by `Point`) are in the vicinity of a 3D `Grid`.  The search radius is `R=radius_factor*(Δx² + Δy² + Δz²)^(1/3)`

`Point` should have 1D coordinate vectors

`Grid_counts` is `Grid` but with an additional field `Count` that has the number of hits
