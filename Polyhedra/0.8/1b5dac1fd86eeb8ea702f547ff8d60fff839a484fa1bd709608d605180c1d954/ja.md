```
surface(p::Polyhedron{T}) where {T}
```

多面体 `p` の表面の `fulldim(p)-1` 次元のハイパーボリュームを返します。型 `T` に無限の値があるかどうかに応じて、無限の場合は `Inf` または `-one(T)` を返します。
