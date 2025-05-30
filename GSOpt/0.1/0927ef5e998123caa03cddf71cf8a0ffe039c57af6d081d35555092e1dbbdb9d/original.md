```
JuMP.set_objective(model::GPModel, sense::MOI.OptimizationSense, func::AbstractGPExpression)
```

Sets the objective function for the geometric programming model.

# Arguments

  * `model::GPModel`: The geometric programming model
  * `sense::MOI.OptimizationSense`: The optimization sense (MIN*SENSE or MAX*SENSE)
  * `func::AbstractGPExpression`: The objective function (must be a posynomial for minimization or a monomial for maximization)

# Throws

  * Error if the objective function is not compatible with the optimization sense
