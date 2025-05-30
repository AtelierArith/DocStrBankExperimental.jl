```
JuMP.set_objective(model::SPModel, sense::MOI.OptimizationSense, func::AbstractGPExpression)
```

Sets the objective function for the signomial programming model.

# Arguments

  * `model::SPModel`: The signomial programming model
  * `sense::MOI.OptimizationSense`: The optimization sense (MIN*SENSE or MAX*SENSE)
  * `func::AbstractGPExpression`: The objective function (must be a signomial for minimization or a monomial for maximization)

# Throws

  * Error if the objective function is not compatible with the optimization sense
