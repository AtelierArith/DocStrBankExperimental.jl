```
sws_eigM(::Type{TR}, s::Integer, c::Complex{TR}, m::Integer, l_max::Integer) where {TR<:AbstractFloat}
sws_eigM!(M::AbstractMatrix{TR}, s::Integer, c::Complex, m::Integer, l_max::Integer) where {TR<:AbstractFloat}
```

Construct the spherical-spheroidal decomposition matrix truncated at l_max.

# Arguments

  * `TR`: Type for floating point conversion
  * `s::Integer`: spin
  * `c::Complex`: oblateness parameter
  * `m::Integer`: azimuthal number
  * `l_max::Integer`: maximum angular number

# References

  * [Cook:2014cta](@citet*)
  * [duetosymmetry/qnm](https://github.com/duetosymmetry/qnm)
