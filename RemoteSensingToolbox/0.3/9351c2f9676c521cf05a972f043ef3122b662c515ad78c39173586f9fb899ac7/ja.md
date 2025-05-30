```
apply_masks(raster, masks...)
```

`Rasters.mask`に似ていますが、以下の違いがあります：

1. 欠損値の代わりに非欠損マスク値を削除します。これは、雲や影のマスクを扱う際に便利です。
2. 複数のマスクを受け入れ、順番に適用されます。

# パラメータ

  * `raster`: マスクを適用する`AbstractRaster`または`AbstractRasterStack`。
  * `masks`: 指定されたラスタに適用する1つ以上のマスク。
