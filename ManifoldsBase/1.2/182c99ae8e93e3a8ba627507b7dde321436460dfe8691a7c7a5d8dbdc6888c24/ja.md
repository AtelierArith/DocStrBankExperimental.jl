```
shortest_geodesic!(M::AabstractManifold, r, p, q, t::Real)
```

[`geodesic`](@ref) $γ_{p,q}(t)$を評価します。これは、点`p`と`q`の間の最短経路の長さを持ち、$γ_{p,q}(0)=p$および$γ_{p,q}(1)=q$で`t`の位置に`r`があります。最短測地線が複数ある場合は、決定論的な選択が行われます。
