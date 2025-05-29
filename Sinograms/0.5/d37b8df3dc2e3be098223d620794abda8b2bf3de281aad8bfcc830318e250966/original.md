```
h, n = fbp_ramp(rg::SinoGeom, N::Int)
```

'ramp-like' filters for parallel-beam and fan-beam FBP reconstruction. This sampled band-limited approach avoids the aliasing that would be caused by sampling the ramp directly in the frequency domain.

# in

  * `rg::SinoGeom`
  * `N::Int` : # of samples (must be even)

# out

  * `h::Vector{<:RealU}` : samples of band-limited ramp filter
  * `n::UnitRange{Int64}` : -(N÷2):(N÷2-1)
