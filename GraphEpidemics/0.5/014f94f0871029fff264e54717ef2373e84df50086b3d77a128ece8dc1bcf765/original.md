`gillespie_sir_direct(g::AbstractGraph, model::AbstractSIRModel, simdata::SIRSimData, rng::AbstractRNG, patient_zeros::Vector{I}; ignore_infector=false, infect_IorS=:I) where I<:Integer`

Runs a SIR simulation using a direct sampling Gillespie method with a binary tree for better event handling. This is NOT the suggested method to use, prefer `sim_sir_gillespie`.

### Optional arguments

  * `ignore_infector`: If true, the simulation does not record who infected each node. Defaults to `false`.
  * `infect_IorS`: Whether infections originate from infected (`:I`) or susceptible (`:S`) nodes. Defaults to `:I`.
