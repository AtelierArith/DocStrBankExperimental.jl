```
Grid_counts = point_to_nearest_grid(pt_x,pt_y,pt_z, Grid::CartData; radius_factor=1)
```

Uses nearest neighbour interpolation to count how many points (given by `pt_x`,`pt_y`,`pt_z` coordinate vectors) are in the  vicinity of 3D `CartGrid` specified by `Grid`. The search radius is `R=radius_factor*(Δx² + Δy² + Δz²)^(1/3)`

`Grid_counts` is `Grid` but with an additional field `Count` that has the number of hits
