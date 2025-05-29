Builds an empty decision model. This constructor is used for the implementation of custom decision models that do not require a template.

# Arguments

  * `::Type{M} where M<:DecisionProblem`: The abstract operation model type
  * `sys::PSY.System`: the system created using Power Systems
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: Enables passing a custom JuMP model. Use with care.

# Example

```julia
problem = DecisionModel(system, optimizer)
```
