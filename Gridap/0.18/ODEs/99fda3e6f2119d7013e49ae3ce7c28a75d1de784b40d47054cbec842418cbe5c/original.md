```
struct TransientTrialFESpace <: SingleFieldFESpace end
```

Transient version of `TrialFESpace`: the Dirichlet boundary conditions are allowed to be time-dependent.

# Mandatory

  * [`allocate_space(space)`](@ref)
  * [`evaluate!(space, t)`](@ref)
  * [`evaluate(space, t)`](@ref)
  * [`time_derivative(space)`](@ref)

# Optional

  * [`evaluate(space, t::Real)`](@ref)
