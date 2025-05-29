```
voxel_grav(X::Array{Float64, 3}, Y::Array{Float64, 3}, Z::Array{Float64, 3}, RHO::Array{Float64, 3};
refMod="AVG", lengthUnit="m", rhoTol=1e-9, Topo=[], outName="Bouguer", printing=true)
```

Computes Bouguer anomalies and gradients

# Required arguments:

  * `X`,`Y`,`Z`:       3D matrices with the coordinates of the grid (X should vary in the first dimension, Y in the second, Z (vertical) in the third)
  * `RHO`:         3D matrix with the density at each grid point [kg/m^3]

# Optional arguments:

  * `refMod`:      1D vector with the reference density for each depth. Alternatively, the strings "NE", "SE", "SW", "NW", "AVG" can be used. In that case, one of the corners of `RHO` is used as reference model.In case of "AVG" the reference model is the average of each depth slice.
  * `lengthUnit`:  The unit of the coordinates and topography file. Either "m" or "km"
  * `rhoTol`:      density differences smaller than `rhoTol` will be ignored [kg/m^3]
  * `Topo`:        2D matrix with the topography of the surface (only relevant for the paraview output)
  * `outName`:     name of the paraview output (do not include file type)
  * `printing`:    activate printing of additional information [`true` or `false`]
