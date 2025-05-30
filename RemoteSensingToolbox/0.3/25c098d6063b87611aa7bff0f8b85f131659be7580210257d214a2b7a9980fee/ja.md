```
forward_pca(transformation::PCA, raster::Union{<:AbstractRaster, <:AbstractRasterStack}, components::Int)
forward_pca(transformation::PCA, signatures::Matrix, components::Int)
```

指定された数の成分のみを保持しながら、前方主成分分析（PCA）回転を実行します。

# パラメータ

  * `transformation`: 以前に適合されたPCA変換。
  * `raster`: PCA変換を実行する`AbstractRaster`または`AbstractRasterStack`。
  * `signatures`: nxbの署名行列で、nは署名の数、bはバンドの数です。
  * `components`: 変換された画像または署名で保持するバンドの数。
