```julia
DecisionModel(
    directory::AbstractString,
    optimizer::MathOptInterface.OptimizerWithAttributes;
    jump_model,
    system
) -> Any

```

Construct an DecisionProblem from a serialized file.

# Arguments

  * `directory::AbstractString`: Directory containing a serialized model
  * `jump_model::Union{Nothing, JuMP.Model}` = nothing: The JuMP model does not get serialized. Callers should pass whatever they passed to the original problem.
  * `optimizer::Union{Nothing,MOI.OptimizerWithAttributes}` = nothing: The optimizer does not get serialized. Callers should pass whatever they passed to the original problem.
  * `system::Union{Nothing, PSY.System}`: Optionally, the system used for the model. If nothing and sys*to*file was set to true when the model was created, the system will be deserialized from a file.
