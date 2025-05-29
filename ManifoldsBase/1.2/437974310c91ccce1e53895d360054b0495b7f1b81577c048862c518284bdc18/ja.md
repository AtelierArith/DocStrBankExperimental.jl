```
shortest_geodesic(M::AbstractManifold, p, q, T::AbstractVector) -> AbstractVector
```

評価する[`geodesic`](@ref) $γ_{p,q}(t)$は、点`p`と`q`の間の最短経路の長さを持ち、$γ_{p,q}(0)=p$および$γ_{p,q}(1)=q$である時間点`T`において定義されます。最短測地線が複数ある場合は、決定論的な選択が返されます。
