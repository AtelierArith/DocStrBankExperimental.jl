```julia
TrackerAdjoint <: AbstractAdjointSensitivityAlgorithm{nothing, true, nothing}
```

An implementation of discrete adjoint sensitivity analysis using the Tracker.jl tracing-based AD. Supports in-place functions through an Array of Structs formulation, and supports out of place through struct of arrays.

## Constructor

```julia
TrackerAdjoint()
```

## SciMLProblem Support

This `sensealg` supports any `DEProblem` if the algorithm is `SciMLBase.isautodifferentiable` Compatible with a limited subset of `AbstractArray` types for `u0`, including `CuArrays`.

!!! warn
    TrackerAdjoint is incompatible with Stiff ODE solvers using forward-mode automatic differentiation for the Jacobians. Thus, for example, `TRBDF2()` will error. Instead, use `autodiff=false`, i.e. `TRBDF2(autodiff=false)`. This will only remove the forward-mode automatic differentiation of the Jacobian construction, not the reverse-mode AD usage, and thus performance will still be nearly the same, though Jacobian accuracy may suffer which could cause more steps to be required.

