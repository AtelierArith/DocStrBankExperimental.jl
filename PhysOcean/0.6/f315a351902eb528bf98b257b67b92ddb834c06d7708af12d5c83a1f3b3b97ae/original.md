```
velocity,ssh,fluxes=geostrophy(mask::BitArray,rhop,pmnin,xiin;dim::Integer=ndims(rhop),ssh=(),znomotion=0,fillin=true)
```

# Input:

  * `mask` : Boolean array with true in water and false on land.
  * `rhop` : density anomaly (rho-1025) array on the same grid as the mask.
  * `pmnin`: tuple of metrics as in divand, but to get velocities in m/s the metrics need to be in per meters too.
  * `xiin`: tuple position of the grid points.
  * `dim` : optional paramter telling which index in the arrays corresponds to the vertical direction. By default the last dimension is used.
  * `ssh` : array as mask for which the vertical direction is taken out. Corresponds to sea surface height in meters. Default is no used but diagnosed
  * `znomotion` : index in the vertical direction where a level of no motion is assumed
  * `fillin` : Boolean telling if a filling of land points using water points at the same level is to be used. Default is yes.

# Output:

  * `velocity` tuple of velocity components NORMAL and to the left of each coordinate line
  * `eta` : sea surface height deduced. If a ssh was provided in input it returs ssh but filled in on land.
  * `fluxes`: integrated velocities across sections in each horizontal direction. Same conventions as for velocities

# Note:

Calculates geostrophic velocities. Works with one or two horizontal dimensions and additional (time) dimensions. Dimensions are supposed to be ordered horizontal, vertical, other dimensions You must either provide the index for the level of no motion or ssh eta. NOTE THAT THE LEVEL IS AN INDEX NUMBER FOR THE MOMENT Dimensions of ssh must be the same as rhop in which vertical dimension has been taken out If you force fillin=false, then you must have created the density array without missing values outside of this call, as well as ssh if you provide it.
