`run_sir_fast(g::AbstractGraph, model::AbstractSIRModel, T::Integer, rng::AbstractRNG, patient_zeros::Vector{<:Integer}; beta_IorS=:I, dtype=Float64, counter=BaseSIRStatesCounter())`

Sets up and runs a fast SIR and SIR-like simulation, returning simulation data and state counts.

The `beta_IorS` argument is used only with the default SIR model (::SIRModel). Other models have their own method for computation of the infection probability.

### Optional arguments

  * `beta_IorS`: Infection rule — whether based on infected (`:I`), susceptible (`:S`), or their average if other value. Defaults to `:I`.
  * `dtype=Float64`: Data type for output arrays.
  * `counter=BaseSIRStatesCounter()`: State counting method.
