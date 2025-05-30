```
mask_nan!(raster)
```

すべての `NaN` 値を `missingval(raster)` でインプレースに置き換えます。

# パラメータ

  * `raster`: `NaN` 値を削除したい `AbstractRaster` または `AbstractRasterStack`。
