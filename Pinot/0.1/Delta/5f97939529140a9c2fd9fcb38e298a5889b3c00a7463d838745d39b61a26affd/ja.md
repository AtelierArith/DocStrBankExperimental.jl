```
transform_position(ops::Vector{Range}, pos) -> Int
```

`ops`によって説明された変更を適用した後の位置の新しい値を返します。挿入の右側に位置を移動します。

```julia
julia> Pinot.transform_position([retain(1), insert("a")], 1) == 2
true
```
