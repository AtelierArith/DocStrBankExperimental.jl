```
CellGrid() <: GridBased <: ConversionTrait
```

`CellGrid` トレイトを持つプロットは、入力データを `(xs::Vector{Float32}, ys::Vector{Float32}, zs::Matrix{Float32})` に変換します。このとき、`(length(xs), length(ys)) == size(zs) .+ 1` となります。変換後、x および y の値は z 値に対応するセルのエッジを表します。

関連情報: [`VertexGrid`](@ref), [`ImageLike`](@ref) 使用目的: ヒートマップ
