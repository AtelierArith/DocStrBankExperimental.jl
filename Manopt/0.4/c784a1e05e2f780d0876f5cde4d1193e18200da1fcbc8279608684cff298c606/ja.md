```
Y = linearized_forward_operator(M::AbstractManifold, N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, m, X, n)
linearized_forward_operator!(M::AbstractManifold, N::AbstractManifold, Y, apdmo::AbstractPrimalDualManifoldObjective, m, X, n)
```

線形化された演算子（微分）$DΛ(m)[X]$を[`AbstractPrimalDualManifoldObjective`](@ref)内に格納された形で評価します（`Y`の代わりに）、ここで$n = Λ(m)$です。
