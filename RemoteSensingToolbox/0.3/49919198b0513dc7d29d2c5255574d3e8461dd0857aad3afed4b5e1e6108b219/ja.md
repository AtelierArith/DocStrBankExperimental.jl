```
inverse_pca(transformation::PCA, raster::AbstractRaster)
inverse_pca(transformation::PCA, signatures::Matrix)
```

元の画像を復元するために逆主成分分析（PCA）変換を実行します。

# パラメータ

  * `transformation`: 以前に適合されたPCA変換。
  * `raster`: 以前に変換された画像を表す`AbstractRaster`。
  * `signatures`: 以前に変換された署名のnxc行列で、nは署名の数、cは成分の数です。
