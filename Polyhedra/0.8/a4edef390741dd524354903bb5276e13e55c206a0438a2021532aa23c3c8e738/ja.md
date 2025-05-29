```
volume(p::Polyhedron{T}) where {T}
```

ポリヘドロン `p` の `fulldim(p)` 次元のハイパーボリュームを返します。型 `T` に無限の値があるかどうかに応じて、無限の場合は `Inf` または `-one(T)` を返します。
