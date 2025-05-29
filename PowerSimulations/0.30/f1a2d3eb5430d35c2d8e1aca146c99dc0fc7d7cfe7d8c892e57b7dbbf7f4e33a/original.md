Builds an empty emulation model. This constructor is used for the implementation of custom emulation models that do not require a template.

# Arguments

  * `::Type{M} where M<:EmulationProblem`: The abstract operation model type
  * `sys::PSY.System`: the system created using Power Systems
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: Enables passing a custom JuMP model. Use with care.

# Example

```julia
problem = EmulationModel(system, optimizer)
```
