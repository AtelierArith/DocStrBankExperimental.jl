```
change_metric(M::AbstractcManifold, G2::AbstractMetric, p, X)
```

On the [`AbstractManifold`](@ref) `M` with implicitly given metric $g_1$ and a second [`AbstractMetric`](@ref) $g_2$ this function performs a change of metric in the sense that it returns the tangent vector $Z=BX$ such that the linear map $B$ fulfills

$$
g_2(Y_1,Y_2) = g_1(BY_1,BY_2) \quad \text{for all } Y_1, Y_2 ∈ T_p\mathcal M.
$$
