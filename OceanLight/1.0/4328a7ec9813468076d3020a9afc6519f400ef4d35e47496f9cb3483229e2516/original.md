```
setwave!(η::Array{<:Float64,2},ηx::Array{<:Float64,2},ηy::Array{<:Float64,2},rms::Float64,p::Param)
```

Giving the value to the existed wave surface distribution grid

# Arguments

  * `η::Array{<:Float64,2}`: water surface elevation.
  * `ηx::Array{<:Float64,2}`: partial derivative of water surface elevation in x direction.
  * `ηy::Array{<:Float64,2}`: partial derivative of water surface elevation in y direction.
  * `rms::Float64`: random number.
  * `p::Param`: simulation parameters.
