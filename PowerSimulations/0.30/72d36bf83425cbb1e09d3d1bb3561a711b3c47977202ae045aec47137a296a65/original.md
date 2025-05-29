```julia
DecisionModel(
    ::Type{M<:PowerSimulations.DecisionProblem},
    template::PowerSimulations.AbstractProblemTemplate,
    sys::PowerSystems.System;
    ...
) -> PowerSimulations.DecisionModel
DecisionModel(
    ::Type{M<:PowerSimulations.DecisionProblem},
    template::PowerSimulations.AbstractProblemTemplate,
    sys::PowerSystems.System,
    jump_model::Union{Nothing, JuMP.Model};
    kwargs...
) -> PowerSimulations.DecisionModel

```

Build the optimization problem of type M with the specific system and template

# Arguments

  * `::Type{M} where M<:DecisionProblem`: The abstract operation model type
  * `template::AbstractProblemTemplate`: The model reference made up of transmission, devices, branches, and services.
  * `sys::PSY.System`: the system created using Power Systems
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: Enables passing a custom JuMP model. Use with care.

# Example

```julia
template = ProblemTemplate(CopperPlatePowerModel, devices, branches, services)
problem = DecisionModel(MyOpProblemType, template, system, optimizer)
```
