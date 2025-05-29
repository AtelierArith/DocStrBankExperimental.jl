`sim_sir_fast(g::AbstractGraph, model::AbstractSIRModel, T::Integer, simdata::SIRSimData, rng::AbstractRNG, patient_zeros::Vector{I}; beta_IorS=:I, counter=BaseSIRStatesCounter()) where I<:Integer`

Runs a discrete-time SIR simulation over `T` time steps, with the data structures already set up.

### Optional arguments

  * `beta_IorS=:I`: Whether to base infection probabilities on infectors (`:I`), susceptibles (`:S`), or their mean. Defaults to `:I`.
  * `counter=BaseSIRStatesCounter()`: The state-counting struct. When using a custom struct, make sure to implement `count_states(::BaseSIRStatesCounter, states::Vector)`
