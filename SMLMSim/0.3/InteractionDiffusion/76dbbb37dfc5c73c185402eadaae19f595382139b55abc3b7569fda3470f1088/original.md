```
DiffusingEmitter2D{T<:AbstractFloat} <: AbstractDiffusingEmitter
```

A 2D emitter type for diffusion simulations that contains both spatial and temporal information, plus molecular state information.

# Fields

  * `x::T`: x-coordinate in microns
  * `y::T`: y-coordinate in microns
  * `photons::T`: number of photons emitted
  * `timestamp::T`: actual simulation time in seconds
  * `frame::Int`: camera frame number based on framerate and exposure
  * `dataset::Int`: dataset identifier
  * `track_id::Int`: unique molecule identifier
  * `state::Symbol`: molecular state (:monomer or :dimer)
  * `partner_id::Union{Int,Nothing}`: ID of linked molecule (for dimers), or nothing for monomers
