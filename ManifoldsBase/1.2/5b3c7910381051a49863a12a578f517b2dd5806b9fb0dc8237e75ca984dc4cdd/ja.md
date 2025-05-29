```
shortest_geodesic(M::AabstractManifold, p, q, t::Real)
```

点 `p` と `q` の間の最短経路の長さを持つ [`geodesic`](@ref) $γ_{p,q}(t)$ を評価します。ここで、$γ_{p,q}(0)=p$ および $γ_{p,q}(1)=q$ であり、時間 `t` において評価されます。最短測地線が複数ある場合は、決定論的な選択が返されます。
