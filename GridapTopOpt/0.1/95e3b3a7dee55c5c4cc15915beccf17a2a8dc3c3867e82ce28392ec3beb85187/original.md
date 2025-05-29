```
PDEConstrainedFunctionals(objective::Function,constraints::Vector{<:Function},
  state_map::AbstractFEStateMap;analytic_dJ;analytic_dC)
```

Create an instance of `PDEConstrainedFunctionals`. The arguments for the objective and constraints must follow the specification in [`StateParamIntegrandWithMeasure`](@ref). By default we use automatic differentation for the objective and all constraints. This can be disabled by passing the shape derivative as a type `Function` to `analytic_dJ` and/or entires in `analytic_dC`.
