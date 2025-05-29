```
Hk = fbp_filter(rg::RayGeom ;
    npad=0, ds::RealU = rg.d, decon1::Bool=true, window=Window())
```

Compute frequency response of ramp-like filter used for FBP image reconstruction. Supports parallel-beam and fan-beam tomographic geometries in 2D and 3D. This code samples the band-limited ramp to avoid the aliasing that would be caused by sampling the ramp directly in the frequency domain.

# in

  * `rg::RayGeom`

# option

  * `npad::Int` # of padded samples. (default: next power of 2)
  * `ds::Td` detector sample spacing (default from `st`)
  * `decon1::Bool` deconvolve effect of linear interpolator? (default: true)
  * `window::Window` apodizer; default: `Window()`

# out

  * `Hk::Vector` apodized ramp filter frequency response
