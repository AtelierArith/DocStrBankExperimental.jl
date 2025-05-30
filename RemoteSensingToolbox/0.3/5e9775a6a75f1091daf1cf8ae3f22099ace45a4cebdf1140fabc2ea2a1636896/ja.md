```
statistics(raster; stats=:all, fraction=1.0)
```

提供された `Raster` または `RasterStack` の要約統計を計算します。

# パラメータ

  * `raster`: `AbstractRaster` または `AbstractRasterStack`。
  * `stats`: :mean, :std, および :cov のシンボルの任意の組み合わせを含む `Vector` または `Tuple`。
  * `fraction`: 統計を計算する際にサンプリングするピクセルの割合。

# 戻り値

要求された各統計を含む名前付きタプル。
