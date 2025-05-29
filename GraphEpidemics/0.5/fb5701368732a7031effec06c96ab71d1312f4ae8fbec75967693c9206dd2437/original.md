`sim_sir_gillespie(g::AbstractGraph, model::AbstractSIRModel, simdata::SIRSimData, rng::AbstractRNG, patient_zeros::Vector{<:Integer}; infect_IorS=:I, max_revive=0, debug=false, counts_func=count_SIR_states)`

Runs a SIR simulation using an optimized Gillespie algorithm and a priority queue.

### Optional arguments

  * `infect_IorS`: Whether infection rates come from infector (`:I`) or susceptible (`:S`) node. Defaults to `:I` (see `get_p_infection`)
  * `max_revive`: Maximum number of times a node can be re-infected after recovery. Defaults to `0`.
  * `debug`: Enables printing of debug information. Defaults to `false`.
  * `counts_func`: Custom function to count states. Defaults to `count_SIR_states`.
