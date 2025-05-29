```
replace_offsets!(g::BVHGraph, h::BVHGraph, exclude::Vector, T::Matrix{Float64} = Matrix(1.0I, 3, 3))
```

`g`のすべての頂点のオフセットを、`exclude`に含まれないものを除いて、`h`の対応する頂点のオフセットに置き換えます。対応する頂点とその隣接頂点は、`g`のものと同じ名前でなければなりません。周囲の頂点の回転が調整されます。`T`は回転行列であり、`g`と`h`のグローバルな向きが異なる場合は提供する必要があります。

関連情報: [`replace_offset!`](@ref), [`project!`](@ref)
