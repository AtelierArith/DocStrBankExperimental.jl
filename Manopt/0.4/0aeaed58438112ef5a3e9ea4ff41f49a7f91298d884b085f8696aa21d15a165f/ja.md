```
q = forward_operator(M::AbstractManifold, N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, p)
forward_operator!(M::AbstractManifold, N::AbstractManifold, q, apdmo::AbstractPrimalDualManifoldObjective, p)
```

[`TwoManifoldProblem`](@ref) に格納されている $Λ(x)$ の前方演算子を評価します（`q` の代わりに）。
