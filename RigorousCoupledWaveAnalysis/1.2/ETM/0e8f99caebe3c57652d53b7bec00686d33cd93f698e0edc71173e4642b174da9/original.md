```
etm_getfields_stack(mdl,grd::RCWAGrid,xypoints,zpoints,λ,a,b,em::Eigenmodes,window,padding)
```

computes the electric and magnetic fields within the whole stack

# Arguments

  * `mdl` : RCWA model object
  * `grd` : reciprocal space grid object
  * `xypoints` : two-element vector specifying the number of points in x, y for which the fields are to be computed (must be even, otherwise truncated)
  * `zpoints` : array of desired z-axis points relative to the top interface of the layer
  * `λ` : wavelength
  * `a` : forward amplitude vectors
  * `b` : backward amplitude vectors
  * `em` : eigenmodes of the layer
  * `window` : type of Window to use against Gibbs' phenomenon, available: Hann (default), None
  * `padding` : padding of the window in x and y, default is [0,0]

# Outputs

  * `efield` : 4D tensor for the electric field (dimensions are x, y, z, and the component (E*x or E*y or E_z)
  * `hfield` : 4D tensor for the magnetic field (dimensions are x, y, z, and the component (E*x or E*y or E_z)
