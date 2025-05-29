```
projection_gradient_on_set(distance_definition, v, s)
```

ベクトル `v` の集合 `s` への射影の勾配を計算します。

各集合 `S` は、メンバーの適切な型の `T` を持つ `projection_gradient_on_set(d::DefaultDistance, v::T, s::S)` を少なくとも実装しています。
