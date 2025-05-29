```
transfer!(ed::Array{<:Float64,3},esol::Array{<:Float64,2},θ::Float64,ϕ::Float64,fres::Float64,ip::Int64,
               xpb::Float64,ypb::Float64,zpb::Float64,area::Vector{Float64},interi::Vector{Int64},
               interj::Vector{Int64},randrng,η::Array{<:Float64,2},ph::Array{<:Float64,1},
               θps::Array{<:Float64,1},p::Param,mode=0::Int64)
```

Doing the Monte Carlo Simulation.

# Arguments

  * `ed::Array{<:Float64,3}`: Irradiance solution grid
  * `esol::Array{<:Float64,2}`: Irradiance solution grid for `solar` mode (under deverlopment)
  * `θ::Float64`: angle of the light ray relative to the z axis: polar angle.
  * `ϕ::Float64`: angle of the light ray relative to the x axis: azimuthal angle.
  * `fres::Float64`: fresnel coefficient or fractional transmission for unpolarized light
  * `ip::Int64`: current photon's number being simulated (ie. ip ∈ {1, 2,..., nphoton})
  * `xpb::Float64`: initial x coordination of the photon.
  * `ypb::Float64`: initial y coordination of the photon.
  * `zpb::Float64`: initial z coordination of the photon.
  * `area::Vector{Float64}`: 4 values of the area inside a single grid where a photon lands corresponding to: 4 corners of the square grid.
  * `interi::Vector{Int64}`: x coordination (grid number) of a single grid where a photon lands: from bottom left, bottom right, upper left, and upper right.
  * `interj::Vector{Int64}`: y coordination (grid number) of a single grid where a photon lands: from bottom left, bottom right, upper left, and upper right.
  * `randrng`: PRNGs (pseudorandom number generators) exported by the Random package.
  * `η::Array{<:Float64,2}`: water surface elevation.
  * `ph::Array{<:Float64,1}`: cumulation distribution of scattering angle (obtained from `phasePetzold()`)
  * `θps::Array{<:Float64,1}`: angle between new trajectory and the direction of the photon before scattering corresponding to each `ϕps` (obtained from `phasePetzold()`)
  * `p::Param`: simulation parameters.
  * `mode::Int64`: mode of different irradinace calculation (under deverlopment)
