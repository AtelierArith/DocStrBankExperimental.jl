```
shortest_geodesic!(M::AbstractManifold, R, p, q, T::AbstractVector) -> AbstractVector
```

[`geodesic`](@ref) $γ_{p,q}(t)$を評価し、`p`と`q`の間の最短経路の長さを持つもので、$γ_{p,q}(0)=p$および$γ_{p,q}(1)=q$となるように、`R`の代わりに`T`のすべての`t`で評価します。最短測地線が複数ある場合は、決定論的な選択が行われます。
