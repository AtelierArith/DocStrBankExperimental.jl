```
ImageLike() <: ConversionTrait
```

`ImageLike`トレイトを持つプロットは、入力データを`(xs::Interval, ys::Interval, zs::Matrix{Float32})`に変換します。ここで、xsとysはzsを含む四角形の限界を示します。

関連情報: [`CellGrid`](@ref), [`VertexGrid`](@ref) 使用目的: 画像
