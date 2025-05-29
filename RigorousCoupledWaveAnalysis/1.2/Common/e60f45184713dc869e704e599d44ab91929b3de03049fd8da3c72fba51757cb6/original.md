```
rcwagrid(Nx,Ny,px,py,θ,α,λ,sup,use_cuda=false)
```

Create a reciprocal space grid for RCWA simulation

# Arguments

  * `nx` : Maximum order in x
  * `ny` : Maximum order in y
  * `px` : Structure pitch in x
  * `py` : Structure pitch in y
  * `θ` : inclination angle of incoming wave
  * `α` : azimuth angle of incoming wave
  * `λ` : wavelength
  * `sup` : superstrate material
  * `use_cuda` : optional, switch to CUDA GPU solver

# Outputs

  * `grd`: RCWA grid struct
