```
count = point_to_nearest_grid(pt_x,pt_y,pt_z, X,Y,Z; radius_factor=1)
```

This uses nearest neighbour interpolation to count how many points (given by `pt_x`,`pt_y`,`pt_z` coordinate vectors) are in the  vicinity of 3D grid point specified by `X`,`Y`,`Z` 3D coordinate arrays, with regular spacing `(Δx,Δy,Δz)`. The search radius is `R=radius_factor*(Δx² + Δy² + Δz²)^(1/3)`
