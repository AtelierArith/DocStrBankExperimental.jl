```
parallel_transport_to(M::AbstractManifold, p, X, q)
```

$$
X
$$

の平行輸送を曲線$c(t) = γ_{p,q}(t)$に沿って計算します。すなわち、点`p`と点`q`を結ぶ（ユニークであると仮定される）[`geodesic`](@ref) $γ_{p,q}$です。
