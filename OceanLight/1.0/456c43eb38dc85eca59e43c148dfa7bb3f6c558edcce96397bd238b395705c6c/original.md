```
transfer!(ed1d::Array{<:Float64,1},edi::Array{<:Int64,1},edj::Array{<:Int64,1},
               edk::Array{<:Int64,1},count::Array{<:Int64,1},esol::Array{<:Float64,2},θ::Float64,ϕ::Float64,fres::Float64,
               ip::Int64,xpb::Float64,ypb::Float64,zpb::Float64,randrng,η::Array{<:Float64,2},
               ph::Array{<:Float64,1},θps::Array{<:Float64,1},p::Param,mode=0::Int64)
```

Doing the Monte Carlo Simulation.

# Arguments

  * `ed1d::Array{<:Float64,1}`: fraction of irradiance that will be assigned to 4 corners of a grid where a photon lands
  * `edi::Array{<:Int64,1}`: x coordination (grid number) of a single grid where a photon lands: from bottom left, bottom right, upper left, and upper right.
  * `edj::Array{<:Int64,1}`: y coordination (grid number) of a single grid where a photon lands: from bottom left, bottom right, upper left, and upper right.
  * `edk::Array{<:Int64,1}`: number of the energy layer that the photons travel, from the top ztop in 1 by 4 array
  * `count::Array{<:Int64,1}`: (parrallel computing) dummy integer span from 1 to 4 to keep track of the size of the ed1d, edi, edj, edk.
  * `esol::Array{<:Float64,2}`:  Irradiance solution grid for `solar` mode (under deverlopment)
  * `θ::Float64`: angle of the light ray relative to the z axis: polar angle.
  * `ϕ::Float64`: angle of the light ray relative to the x axis: azimuthal angle.
  * `fres::Float64`: fresnel coefficient or fractional transmission for unpolarized light.
  * `ip::Int64`: current photon's number being simulated (ie. ip ∈ {1, 2,..., nphoton})
  * `xpb::Float64`: initial x coordination of the photon.
  * `ypb::Float64`: initial y coordination of the photon.
  * `zpb::Float64`: initial z coordination of the photon.
  * `randrng`: PRNGs (pseudorandom number generators) exported by the Random package
  * `η::Array{<:Float64,2}`: water surface elevation.
  * `ph::Array{<:Float64,1}`: cumulation distribution of scattering angle (obtained from `phasePetzold()`)
  * `θps::Array{<:Float64,1}`: angle between new trajectory and the direction of the photon before scattering corresponding to each `ϕps` (obtained from `phasePetzold()`)
  * `p::Param`: simulation parameters.
  * `mode::Int64`: mode of different irradinace calculation (under deverlopment)
