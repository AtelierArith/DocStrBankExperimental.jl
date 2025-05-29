```julia
struct UnconstrainedObjective{D<:Cthonios.Domain, I<:Cthonios.AbstractIntegral, T} <: Cthonios.AbstractObjective
```

  * `domain::Cthonios.Domain`
  * `integral::Cthonios.AbstractIntegral`
  * `timer::Any`

Objective type for evaluating objective functions. The functions correspond to quadrature level evaluations of the objective function, it's gradient, and it's hessian respectively. `domain` - A domain object  `integral` - An AbstractIntegral `timer` - A timer that's already setup.
