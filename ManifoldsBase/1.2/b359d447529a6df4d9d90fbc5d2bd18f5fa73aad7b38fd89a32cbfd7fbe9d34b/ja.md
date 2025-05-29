```
shortest_geodesic(M::AbstractManifold, p, q) -> Function
```

最短経路である点 `p` と `q` の間の長さを持つ [`geodesic`](@ref) $γ_{p,q}(t)$ を取得します。ここで、$γ_{p,q}(0)=p$ および $γ_{p,q}(1)=q$ です。最短の測地線が複数ある場合は、決定論的な選択が返されます。

この関数は、`Real` または `AbstractVector` である可能性のある時間の関数を返します。
