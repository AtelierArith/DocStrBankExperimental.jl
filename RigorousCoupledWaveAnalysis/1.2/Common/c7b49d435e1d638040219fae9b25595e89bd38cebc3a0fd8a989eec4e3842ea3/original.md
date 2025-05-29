```
getfields(ain,bout,em::Eigenmodes,grd::RCWAGrid,xypoints,zpoints,λ,window,padding)
```

computes the electric and magnetic fields within a layer

# Arguments

  * `ain` : amplitude vector entering the layer from the previous layer
  * `bout` : amplitude vector leaving the layer towards the previous layer
  * `em` : eigenmodes of the layer
  * `grd` : reciprocal space grid object
  * `xypoints` : two-element vector specifying the number of points in x, y for which the fields are to be computed, better even numbers, otherwise truncated to even
  * `zpoints` : array of desired z-axis points relative to the top interface of the layer
  * `λ` : wavelength
  * `window` : type of Window to use against Gibbs' phenomenon, available: Hann (default), None
  * `padding` : padding of the window in x and y, default is [0,0], not yet implemented

# Outputs

  * `efield` : 4D tensor for the electric field (dimensions are x, y, z, and the component (E*x or E*y or E_z)
  * `hfield` : 4D tensor for the magnetic field (dimensions are x, y, z, and the component (E*x or E*y or E_z)
