```
dem2particle(dem, h, bottom, layer)
```

## Description:

Generate particles from a given DEM file and a bottom value (flat bottom surface). `dem` is  a coordinates Array with three columns (x, y, z), and the `bottom` value should be lower than the dem. `h` is the space of grid size in `z` direction used in the MPM simulation. `layer` is a Vector of Matrix with three columns (x, y, z), which represents the layer surfaces. Note that layers are sorted from top to bottom.
