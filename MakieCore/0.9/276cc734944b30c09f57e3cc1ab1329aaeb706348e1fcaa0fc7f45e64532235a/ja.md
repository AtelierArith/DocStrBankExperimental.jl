```
VertexGrid() <: GridBased <: ConversionTrait
```

`VertexGrid` トレイトを持つプロットは、入力データを `(xs::Vector{Float32}, ys::Vector{Float32}, zs::Matrix{Float32})` に変換します。このとき、`(length(xs), length(ys)) == size(zs)` であるか、または `(xs::Matrix{Float32}, ys::Matrix{Float32}, zs::Matrix{Float32})` に変換され、`size(xs) == size(ys) == size(zs)` である必要があります。

参照: [`CellGrid`](@ref), [`ImageLike`](@ref) 使用目的: Surface
