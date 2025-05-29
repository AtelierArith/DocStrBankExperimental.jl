```
Y = linearized_forward_operator(M::AbstractManifold, N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, m, X, n)
linearized_forward_operator!(M::AbstractManifold, N::AbstractManifold, Y, apdmo::AbstractPrimalDualManifoldObjective, m, X, n)
```

Evaluate the linearized operator (differential) $DΛ(m)[X]$ stored within the [`AbstractPrimalDualManifoldObjective`](@ref) (in place of `Y`), where `n = Λ(m)`.
