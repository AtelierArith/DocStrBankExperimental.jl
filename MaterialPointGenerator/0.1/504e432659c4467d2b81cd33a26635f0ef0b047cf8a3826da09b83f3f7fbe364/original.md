```
dem2particle(dem, h, bottom)
```

## Description:

Generate particles from a given DEM file. `dem` is a coordinates Array with three columns  (x, y, z). `h` is the space of particles in `z` direction, normally it is equal to the grid  size in the MPM simulation. `bottom` is a value, which means the plane `z = bottom`.
