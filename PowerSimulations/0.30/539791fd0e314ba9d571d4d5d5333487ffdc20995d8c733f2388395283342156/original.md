```julia
EmulationModel(
    ::Type{M<:PowerSimulations.EmulationProblem},
    template::PowerSimulations.AbstractProblemTemplate,
    sys::PowerSystems.System;
    ...
) -> PowerSimulations.EmulationModel
EmulationModel(
    ::Type{M<:PowerSimulations.EmulationProblem},
    template::PowerSimulations.AbstractProblemTemplate,
    sys::PowerSystems.System,
    jump_model::Union{Nothing, JuMP.Model};
    kwargs...
) -> PowerSimulations.EmulationModel

```

Build the optimization problem of type M with the specific system and template

# Arguments

  * `::Type{M} where M<:EmulationProblem`: The abstract Emulation model type
  * `template::AbstractProblemTemplate`: The model reference made up of transmission, devices, branches, and services.
  * `sys::PSY.System`: the system created using Power Systems
  * `jump_model::Union{Nothing, JuMP.Model}`: Enables passing a custom JuMP model. Use with care

# Example

```julia
template = ProblemTemplate(CopperPlatePowerModel, devices, branches, services)
problem = EmulationModel(MyEmProblemType, template, system, optimizer)
```
