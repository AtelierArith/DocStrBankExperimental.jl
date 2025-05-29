```
X = adjoint_linearized_operator(N::AbstractManifold, apdmo::AbstractPrimalDualManifoldObjective, m, n, Y)
adjoint_linearized_operator(N::AbstractManifold, X, apdmo::AbstractPrimalDualManifoldObjective, m, n, Y)
```

$$
(DΛ(m))^*[Y]
$$

の線形化された前方演算子の随伴を評価します。これは [`AbstractPrimalDualManifoldObjective`](@ref) 内に格納されており、`X` の代わりに使用されます。$Y∈T_n\mathcal N$ であるため、$m$ と $n=Λ(m)$ は必要な引数です。主に、前方演算子 $Λ$ が `p` において `missing` である可能性があるためです。
