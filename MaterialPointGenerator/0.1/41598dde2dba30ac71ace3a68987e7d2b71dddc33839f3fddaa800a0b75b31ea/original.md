```
dem2particle(dem, h, bottom)
```

## Description:

Generate particles from a given DEM file and a bottom surface file. `dem` is a coordinates  Array with three columns (x, y, z), which has to be initialized with the struct `DEMSurface`.  `bottom::DEMSurface` should have the same x and y coordinates as the DEM, and the z value should be lower than the dem. `h` is the space of grid size in `z` direction used in the MPM simulation.
