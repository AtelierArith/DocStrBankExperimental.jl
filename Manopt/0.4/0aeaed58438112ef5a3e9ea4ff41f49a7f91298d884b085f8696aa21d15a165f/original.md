```
q = forward_operator(M::AbstractManifold, N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, p)
forward_operator!(M::AbstractManifold, N::AbstractManifold, q, apdmo::AbstractPrimalDualManifoldObjective, p)
```

Evaluate the forward operator of $Λ(x)$ stored within the [`TwoManifoldProblem`](@ref) (in place of `q`).
