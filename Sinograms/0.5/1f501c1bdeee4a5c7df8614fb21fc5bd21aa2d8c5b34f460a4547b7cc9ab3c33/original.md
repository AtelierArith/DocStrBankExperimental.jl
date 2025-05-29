```
sino = fbp_sino_filter(sino::Array, filter::Vector ; extra=0)
```

Apply ramp-like filters to sinogram(s) for 2D FBP image reconstruction. Supports both parallel-beam and fan-beam tomographic geometries in 2D and 3D.

# in

  * `sino::AbstractArray{<:Number}` `[nb (L)]` sinograms
  * `filter::AbstractVector` `(npad ≥ nb)` apodized ramp filter frequency response

# option

  * `extra::Int` # of extra sinogram radial samples to keep (default: 0)
  * `npad::Int` # of padded samples. (default: next power of 2)

# out

  * `sino::AbstractArray` sinogram with filtered rows
