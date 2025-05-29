```
AbstractRasterSeries <: DimensionalData.AbstractDimensionalArray
```

`RasterStacks`、`Rasters`、またはそれらを読み込むことができるパスを保持する高レベルの `DimensionalArray` の抽象スーパタイプです。`RasterSeries` は `AbstractRaster` と同様に次元でインデックス付けされます。これは、時間や標高のような次元に広がるラスタやラスタのスタックを含む複数のファイルがある場合に便利です。

可能な限り、実装はディレクトリ全体の読み込みとメタデータからの次元の検出を容易にするべきです。

これにより、配列のスタックのシリーズに対して以下のような構文が可能になります：

```julia
RasterSeries[Time(Near(DateTime(2001, 1))][:temp][Y(Between(70, 150)), X(Between(-20,20))] |> plot`
```

[`RasterSeries`](@ref) は具体的な実装です。
