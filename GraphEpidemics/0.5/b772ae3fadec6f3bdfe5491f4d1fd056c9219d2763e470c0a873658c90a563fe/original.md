`run_sir_gillespie(g::AbstractGraph, model::AbstractSIRModel, rng::AbstractRNG, patient_zeros::Vector{<:Integer}; dtype=Float64, kwargs...)`

Sets up simulation data and runs a Gillespie SIR simulation with recovery delays drawn according to the model.

### Optional arguments

  * `dtype`: Data type for the simulation arrays. Defaults to `Float64`.
