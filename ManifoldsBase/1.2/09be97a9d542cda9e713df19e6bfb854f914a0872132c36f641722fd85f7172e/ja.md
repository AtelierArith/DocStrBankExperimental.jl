```
change_metric(M::AbstractcManifold, G2::AbstractMetric, p, X)
```

[`AbstractManifold`](@ref) `M` 上で、暗黙的に与えられた計量 $g_1$ と第二の [`AbstractMetric`](@ref) $g_2$ に対して、この関数は計量の変更を行い、線形写像 $B$ が満たすような接ベクトル $Z=BX$ を返します。

$$
g_2(Y_1,Y_2) = g_1(BY_1,BY_2) \quad \text{for all } Y_1, Y_2 ∈ T_p\mathcal M.
$$
