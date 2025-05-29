Temperature relaxation from Held and Suarez, 1996 BAMS

  * `nlat::Int64`: number of latitude rings
  * `nlayers::Int64`: number of vertical levels
  * `σb::AbstractFloat`: sigma coordinate below which faster surface relaxation is applied
  * `relax_time_slow::Dates.Second`: time scale for slow global relaxation
  * `relax_time_fast::Dates.Second`: time scale for faster tropical surface relaxation
  * `Tmin::AbstractFloat`: minimum equilibrium temperature [K]
  * `Tmax::AbstractFloat`: maximum equilibrium temperature [K]
  * `ΔTy::AbstractFloat`: meridional temperature gradient [K]
  * `Δθz::AbstractFloat`: vertical temperature gradient [K]
  * `κ::Base.RefValue{NF} where NF<:AbstractFloat`
  * `p₀::Base.RefValue{NF} where NF<:AbstractFloat`
  * `temp_relax_freq::Matrix{NF} where NF<:AbstractFloat`
  * `temp_equil_a::Vector{NF} where NF<:AbstractFloat`
  * `temp_equil_b::Vector{NF} where NF<:AbstractFloat`
