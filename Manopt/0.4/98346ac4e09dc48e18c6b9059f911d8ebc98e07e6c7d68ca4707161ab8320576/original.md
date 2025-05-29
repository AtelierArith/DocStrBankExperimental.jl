```
X = adjoint_linearized_operator(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, m, n, Y)
adjoint_linearized_operator(N::AbstractManifold, X, apdmo::AbstractPrimalDualManifoldObjective, m, n, Y)
```

Evaluate the adjoint of the linearized forward operator of $(DΛ(m))^*[Y]$ stored within the [`AbstractPrimalDualManifoldObjective`](@ref) (in place of `X`). Since $Y∈T_n\mathcal N$, both $m$ and $n=Λ(m)$ are necessary arguments, mainly because the forward operator $Λ$ might be `missing` in `p`.
