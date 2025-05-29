```
shortest_geodesic!(M::AbstractManifold, p, q) -> Function
```

点 `p` と `q` の間の最短経路の長さを持つ [`geodesic`](@ref) $γ_{p,q}(t)$ を取得します。ここで、$γ_{p,q}(0)=p$ および $γ_{p,q}(1)=q$ です。最短の測地線が複数ある場合は、決定論的な選択が返されます。

この関数は、時間 `t` の `(r,t) -> ...` という関数を返し、`r` の代わりに機能します。

さらなるバリアント

```
shortest_geodesic!(M::AabstractManifold, r, p, q, t::Real)
shortest_geodesic!(M::AbstractManifold, R, p, q, T::AbstractVector) -> AbstractVector
```

それぞれ、点 `r` と点のベクトル `R` を変異させ（および返し）、最短の [`geodesic`](@ref) に沿った時間 `t` での点または時間 `T` での点を返します。
