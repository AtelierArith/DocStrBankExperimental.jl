```julia
ReverseDiffAdjoint <: AbstractAdjointSensitivityAlgorithm{nothing, true, nothing}
```

An implementation of discrete adjoint sensitivity analysis using the ReverseDiff.jl tracing-based AD. Supports in-place functions through an Array of Structs formulation, and supports out of place through struct of arrays.

## Constructor

```julia
ReverseDiffAdjoint()
```

## SciMLProblem Support

This `sensealg` supports any `DEProblem` if the algorithm is `SciMLBase.isautodifferentiable`. Requires that the state variables are CPU-based `Array` types.
