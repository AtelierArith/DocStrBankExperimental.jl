```
AbstractRaster <: DimensionalData.AbstractDimArray
```

配列（または配列の位置）とその内容に関するメタデータをラップするオブジェクトのための抽象スーパタイプです。これはメモリを持つか、ファイル名を保持する `FileArray` を持ち、必要なときにのみ開かれます。

`AbstractRaster` は、DimensionalData.jl の [`AbstractDimArray`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.AbstractDimArray) から継承されます。通常の Julia 配列として、または DimensionalData.jl の [`Dimension`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Dimension) でインデックス指定できます。`getindex` や `view` でスライスした後でも、正しい座標とラベルで Plots.jl でヒートマップとしてプロットされます。`AbstractRaster` の `getindex` は常にメモリバックの `Raster` を返します。
