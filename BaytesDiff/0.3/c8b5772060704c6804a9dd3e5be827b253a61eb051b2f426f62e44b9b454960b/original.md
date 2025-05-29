```julia
struct AnalyticalDiffTune{G<:Function, H<:Union{Nothing, Function}} <: BaytesDiff.AbstractDifferentiableTune
```

Stores information for evaluating and taking the gradient of an objective function.

# Fields

  * `gradient::Function`: Gradient as function of ℓobjective and parameter vector in unconstrained space, gradient(ℓobjective, θᵤ).
  * `hessian::Union{Nothing, Function}`: Hessian as function of ℓobjective and parameter vector in unconstrained space, hessian(ℓobjective, θᵤ).
