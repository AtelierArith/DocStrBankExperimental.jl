```
sample(m::MPS)
```

正規化された MPS m が `orthocenter(m)==1` の場合、MPS が表すテンソルの成分を二乗することによって定義される確率分布のサンプルに対応する `length(m)` の `Vector{Int}` を返します。
