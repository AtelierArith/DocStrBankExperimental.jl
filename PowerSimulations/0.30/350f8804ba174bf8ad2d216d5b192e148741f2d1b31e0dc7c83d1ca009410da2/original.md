```
DecisionModel{M}(
    template::AbstractProblemTemplate,
    sys::PSY.System,
    jump_model::Union{Nothing, JuMP.Model}=nothing;
    kwargs...) where {M<:DecisionProblem}
```

Build the optimization problem of type M with the specific system and template.

# Arguments

  * `::Type{M} where M<:DecisionProblem`: The abstract operation model type
  * `template::AbstractProblemTemplate`: The model reference made up of transmission, devices, branches, and services.
  * `sys::PSY.System`: the system created using Power Systems
  * `jump_model::Union{Nothing, JuMP.Model}`: Enables passing a custom JuMP model. Use with care
  * `name = nothing`: name of model, string or symbol; defaults to the type of template converted to a symbol.
  * `optimizer::Union{Nothing,MOI.OptimizerWithAttributes} = nothing` : The optimizer does not get serialized. Callers should pass whatever they passed to the original problem.
  * `horizon::Dates.Period = UNSET_HORIZON`: Manually specify the length of the forecast Horizon
  * `resolution::Dates.Period = UNSET_RESOLUTION`: Manually specify the model's resolution
  * `warm_start::Bool = true`: True will use the current operation point in the system to initialize variable values. False initializes all variables to zero. Default is true
  * `system_to_file::Bool = true:`: True to create a copy of the system used in the model.
  * `initialize_model::Bool = true`: Option to decide to initialize the model or not.
  * `initialization_file::String = ""`: This allows to pass pre-existing initialization values to avoid the solution of an optimization problem to find feasible initial conditions.
  * `deserialize_initial_conditions::Bool = false`: Option to deserialize conditions
  * `export_pwl_vars::Bool = false`: True to export all the pwl intermediate variables. It can slow down significantly the build and solve time.
  * `allow_fails::Bool = false`: True to allow the simulation to continue even if the optimization step fails. Use with care.
  * `optimizer_solve_log_print::Bool = false`: Uses JuMP.unset_silent() to print the optimizer's log. By default all solvers are set to MOI.Silent()
  * `detailed_optimizer_stats::Bool = false`: True to save detailed optimizer stats log.
  * `calculate_conflict::Bool = false`: True to use solver to calculate conflicts for infeasible problems. Only specific solvers are able to calculate conflicts.
  * `direct_mode_optimizer::Bool = false`: True to use the solver in direct mode. Creates a [JuMP.direct_model](https://jump.dev/JuMP.jl/dev/reference/models/#JuMP.direct_model).
  * `store_variable_names::Bool = false`: to store variable names in optimization model. Decreases the build times.
  * `rebuild_model::Bool = false`: It will force the rebuild of the underlying JuMP model with each call to update the model. It increases solution times, use only if the model can't be updated in memory.
  * `initial_time::Dates.DateTime = UNSET_INI_TIME`: Initial Time for the model solve.
  * `time_series_cache_size::Int = IS.TIME_SERIES_CACHE_SIZE_BYTES`: Size in bytes to cache for each time array. Default is 1 MiB. Set to 0 to disable.

# Example

```julia
template = ProblemTemplate(CopperPlatePowerModel, devices, branches, services)
OpModel = DecisionModel(MockOperationProblem, template, system)
```
