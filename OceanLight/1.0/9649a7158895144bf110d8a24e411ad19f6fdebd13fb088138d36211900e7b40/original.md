```
interface!(xpb::Array{<:Float64,2},ypb::Array{<:Float64,2},zpb::Array{<:Float64,2},
                θ::Array{<:Float64,2},ϕ::Array{<:Float64,2},fres::Array{<:Float64,2},
                η::Array{<:Float64,2},ηx::Array{<:Float64,2},ηy::Array{<:Float64,2},p::Param)
```

Calculate the reflection and refraction of the photon or light ray that transmit from the atmosphere to the water.

# Arguments

  * `xpb::Array{<:Float64,2}`: initial x coordination of the photon.
  * `ypb::Array{<:Float64,2}`: initial y coordination of the photon.
  * `zpb::Array{<:Float64,2}`: initial z coordination of the photon.
  * `θ::Array{<:Float64,2}`: angle of the light ray relative to the z axis: polar angle.
  * `ϕ::Array{<:Float64,2}`: angle of the light ray relative to the x axis: azimuthal angle.
  * `fres::Array{<:Float64,2}`: fresnel coefficient or fractional transmission for unpolarized light
  * `η::Array{<:Float64,2}`: water surface elevation.
  * `ηx::Array{<:Float64,2}`: partial derivative of water surface elevation in x direction.
  * `ηy::Array{<:Float64,2}`: partial derivative of water surface elevation in y direction.
  * `p::Param`: simulation parameters.
