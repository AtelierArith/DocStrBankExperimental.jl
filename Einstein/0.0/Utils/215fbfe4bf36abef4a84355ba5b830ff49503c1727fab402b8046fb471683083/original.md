```
sws_eigen(::Type{TR}, s::Integer, c::Complex{TR}, m::Integer, l_max::Integer) where {TR<:AbstractFloat}
```

Calculate eigenvalues and eigenvectors of the spherical-spheroidal decomposition matrix.

# Arguments

  * `TR`: Type for floating point conversion
  * `s::Integer`: spin
  * `c::Complex`: oblateness parameter
  * `m::Integer`: azimuthal number
  * `l_max::Integer`: maximum angular number

# References

  * [Cook:2014cta](@citet*)
  * [duetosymmetry/qnm](https://github.com/duetosymmetry/qnm)
