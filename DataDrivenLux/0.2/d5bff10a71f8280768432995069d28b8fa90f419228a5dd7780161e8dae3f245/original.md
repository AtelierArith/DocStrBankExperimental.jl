```julia
struct Candidate{__T_rng<:Random.AbstractRNG, __T_st<:NamedTuple, __T_ps<:(AbstractVector), __T_incoming_path<:(Vector{<:DataDrivenLux.AbstractPathState}), __T_outgoing_path<:(Vector{<:DataDrivenLux.AbstractPathState}), __T_statistics<:DataDrivenLux.PathStatistics, __T_observed<:DataDrivenLux.ObservedModel, __T_parameterdist<:DataDrivenLux.ParameterDistributions, __T_scales<:(AbstractVector), __T_parameters<:(AbstractVector), __T_model<:DataDrivenLux.ComponentModel} <: StatsAPI.StatisticalModel
```

A container holding all the information for the current candidate solution to the symbolic regression problem.

# Fields

  * `rng`: Random seed
  * `st`: The current state
  * `ps`: The current parameters
  * `incoming_path`: Incoming paths
  * `outgoing_path`: Outgoing path
  * `statistics`: Statistics
  * `observed`: The observed model
  * `parameterdist`: The parameter distribution
  * `scales`: The optimal scales
  * `parameters`: The optimal parameters
  * `model`: The component model
