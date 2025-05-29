```
RefractivePhaseScreen(sm, Nx, Ny, dx, dy, Vx_km_per_s=0.0, Vy_km_per_s=0.0)
```

An abstract type for generating a refractive phase screen model corresponding to an image and computing the scattered average image.

  * `sm <: AbstractScatteringModel`
  * `Nx`: image size in x axis
  * `Ny`: image size in y axis
  * `dx`: pixel size in x direction (in radians)
  * `dy`: pixel size in y direction (in radians)

`Vx_km_per_s` and `Vy_km_per_s` are optional for moving phase screen. 
