```
excitations(H, algorithm::QuasiparticleAnsatz, left_ψ::InfiniteMPS, [left_environment],
            [right_ψ::InfiniteMPS], [right_environment]; kwargs...)
```

Create and optimise finite quasiparticle states.

# Arguments

  * `H::AbstractMPO`: operator for which to find the excitations
  * `algorithm::QuasiparticleAnsatz`: optimization algorithm
  * `left_ψ::FiniteMPS`: left groundstate
  * `[left_environment]`: left groundstate environment
  * `[right_ψ::FiniteMPS]`: right groundstate
  * `[right_environment]`: right groundstate environment

# Keywords

  * `num::Int`: number of excited states to compute
  * `sector=one(sectortype(left_ψ))`: charge of the quasiparticle state
