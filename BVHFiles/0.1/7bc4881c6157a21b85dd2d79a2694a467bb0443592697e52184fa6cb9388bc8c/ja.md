```
replace_offset!(g::BVHGraph, h::BVHGraph, gv₊₁::Integer, T::Matrix{Float64} = Matrix(1.0I, 3, 3); change_rotation::Bool = true)
```

`g`の頂点`gv₊₁`のオフセットを`h`の対応する頂点のオフセットに置き換えます。対応する頂点とその隣接頂点は、`g`のものと同じ名前でなければなりません。周囲の頂点の回転が調整されます。`T`は、`g`と`h`のグローバルな向きが異なる場合に提供されるべき回転行列です。

参照: [`replace_offsets!`](@ref), [`project!`](@ref)
