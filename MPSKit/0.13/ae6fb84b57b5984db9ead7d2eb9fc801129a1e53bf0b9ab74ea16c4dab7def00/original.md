```
excitations(H, algorithm::QuasiparticleAnsatz, momentum::Union{Number, Vector{<:Number}},
            left_ψ::InfiniteMPS, [left_environment],
            [right_ψ::InfiniteMPS], [right_environment];
            kwargs...)
```

Create and optimise infinite quasiparticle states.

# Arguments

  * `H::AbstractMPO`: operator for which to find the excitations
  * `algorithm::QuasiparticleAnsatz`: optimization algorithm
  * `momentum::Union{Number, Vector{<:Number}}`: momentum or list of momenta
  * `left_ψ::InfiniteMPS`: left groundstate
  * `[left_environment]`: left groundstate environment
  * `[right_ψ::InfiniteMPS]`: right groundstate
  * `[right_environment]`: right groundstate environment

# Keywords

  * `num::Int`: number of excited states to compute
  * `solver`: algorithm for the linear solver of the quasiparticle environments
  * `sector=one(sectortype(left_ψ))`: charge of the quasiparticle state
  * `parallel=true`: enable multi-threading over different momenta
