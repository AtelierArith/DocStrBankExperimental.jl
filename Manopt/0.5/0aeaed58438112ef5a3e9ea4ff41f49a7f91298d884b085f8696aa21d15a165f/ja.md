```
q = forward_operator(M::AbstractManifold, N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, p)
forward_operator!(M::AbstractManifold, N::AbstractManifold, q, apdmo::AbstractPrimalDualManifoldObjective, p)
```

$$
Λ(x)
$$

内の前方演算子を評価します [`TwoManifoldProblem`](@ref) （`q`の代わりに）。
