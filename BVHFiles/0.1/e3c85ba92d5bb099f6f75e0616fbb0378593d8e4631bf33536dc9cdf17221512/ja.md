```
project!(g::BVHGraph, h::BVHGraph, T::Matrix = Matrix(1.0I, 3, 3))
```

`h`の各頂点の回転を、対応する`g`の頂点に転送します。対応する頂点は同じ名前でなければなりません。`T`は回転行列で、`g`と`h`のグローバルな向きが異なる場合に提供する必要があります。

参照: [`replace_offset!`](@ref), [`replace_offsets!`](@ref)
