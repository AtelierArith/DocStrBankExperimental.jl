```
fit_pca(raster::Union{<:AbstractRasterStack, <:AbstractRaster}; method=:cov, stats_fraction=1.0)
fit_pca(signatures::Matrix; method=:cov, stats_fraction=1.0)
```

与えられたラスタまたはスペクトル署名に主成分分析（PCA）変換を適合させます。

# パラメータ

  * `raster`: PCA変換を適合させる`AbstractRaster`または`AbstractRasterStack`。
  * `signatures`: スペクトル署名のnxb行列で、nは署名の数、bはバンドの数です。

# キーワード

  * `method`: `:cov`または`:cor`のいずれかで、PCA回転を計算するために共分散行列または相関行列を使用するかどうかを決定します。
  * `stats_fraction`: 共分散（または相関）行列を計算する際に使用するピクセルの割合。1.0未満の値は、精度を犠牲にして計算を高速化します。
