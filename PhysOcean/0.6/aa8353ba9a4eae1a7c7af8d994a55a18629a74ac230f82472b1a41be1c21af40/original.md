```
psifluxes=streamfunctionvolumeflux(mask::BitArray,velocities,pmnin,xiin;dim::Integer=ndims(mask))
```

# Input:

  * `mask` : Boolean array with true in water and false on land.
  * `velocities` : tuple of arrays on the same grid as the mask. Each tuple element is a velocity field normal to the corresponding direction in space
  * `pmnin`: tuple of metrics as in divand, but to get velocities in m/s the metrics need to be in per meters too.
  * `xiin`: tuple position of the grid points.
  * `dim` : optional paramter telling which index in the arrays corresponds to the vertical direction. By default the last dimension is used.

# Output:

  * `psifluxes` tuple of volume fluxes at each depth and direction NORMAL and to the left of each coordinate line

Calculates volume flux streamfunction calculated from the surface. The value of this field provides the total flow (in Sverdrup) across the section above the depth of the zlevel looked at.
