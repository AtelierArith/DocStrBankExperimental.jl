```
Scenario(
  model::Model,
  tspan;
  measurements::Vector{AbstractMeasurementPoint}=AbstractMeasurementPoint[],
  observables::Union{Nothing,Vector{Symbol}}=nothing,
  parameters::AbstractVector{<:Pair{Symbol,<:Real}} = Pair{Symbol,Float64}[],
  events_active::Union{Nothing, Vector{Pair{Symbol,Bool}}} = Pair{Symbol,Bool}[],
  events_save::Union{Tuple,Vector{Pair{Symbol, Tuple{Bool, Bool}}}} = (true,true),
  saveat::Union{Nothing,AbstractVector} = nothing,

  save_scope::Bool = true,
)
```

Builds simulation scenario of type [`Scenario`](@ref)

Example: `Scenario(model, (0., 200.))`

Arguments:

  * `model` : model of type [`Model`](@ref)
  * `tspan` : time span for the ODE problem
  * `measurements` : `Vector` of measurements. Default is empty `Vector{AbstractMeasurementPoint}`
  * `observables` : names of output observables. Overwrites default model's values. Default is `nothing`
  * `tags` :
  * `group` :
  * `parameters` : `Vector` of `Pair`s containing parameters' names and values. Overwrites default model's values. Default is empty vector.
  * `events_active` : `Vector` of `Pair`s containing events' names and true/false values. Overwrites default model's values. Default is empty `Vector{Pair}`
  * `events_save` : `Tuple` or `Vector{Tuple}` marking whether to save solution before and after event. Default is `(true,true)` for all events
  * `saveat` : time points, where solution should be saved. Default `nothing` values stands for saving solution at timepoints reached by the solver
  * `save_scope` : should scope be saved together with solution. Default is `true`
