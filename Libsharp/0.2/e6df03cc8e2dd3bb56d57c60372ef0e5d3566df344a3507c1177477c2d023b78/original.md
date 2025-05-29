```
sharp_execute!(args...) where T <: AbstractFloat
```

Performs a libsharp2 SHT job.

For a spin 0 field, maps[1] should be the array of containing the map elements. Similarly, for a spin 2 field, maps[1] and maps[2] contain the two spin-2  components. The alms are in a similar format, i.e. alms[1] and alms[2] are the  harmonics describing a spin-2 field.

You should specify `flags=0` for single precision and `flags=SHARP_DP` for double precision.

# Arguments

  * `jobtype::Integer`: libsharp job type
  * `spin::Integer`: spin of the field
  * `alms::Array{Array{Complex{T},1},1}`: alm arrays
  * `maps::Array{Array{T,1},1}`: map arrays
  * `geom_info::GeomInfo`: pixelisation info
  * `alm_info::AlmInfo`: spherical harmonic coefficients info
  * `flags::Integer`: additional flags
