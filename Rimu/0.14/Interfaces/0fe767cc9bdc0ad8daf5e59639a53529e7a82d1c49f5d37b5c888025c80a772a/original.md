```
LOStructure(op::AbstractHamiltonian)
LOStructure(typeof(op))
```

Return information about the structure of the linear operator `op`. `LOStructure` is used as a trait to speficy symmetries or other properties of the linear operator `op` that may simplify or speed up calculations. Implemented instances are:

  * `IsDiagonal()`: The operator is diagonal.
  * `IsHermitian()`: The operator is complex and Hermitian or real and symmetric.
  * `AdjointKnown()`: The operator is not Hermitian, but its   [`adjoint`](@ref Main.Hamiltonians.adjoint) is implemented.
  * `AdjointUnknown()`: [`adjoint`](@ref Main.Hamiltonians.adjoint) for this operator is not   implemented.

Part of the [`AbstractHamiltonian`](@ref) interface.

In order to define this trait for a new linear operator type, define a method for `LOStructure(::Type{<:MyNewLOType}) = …`.
