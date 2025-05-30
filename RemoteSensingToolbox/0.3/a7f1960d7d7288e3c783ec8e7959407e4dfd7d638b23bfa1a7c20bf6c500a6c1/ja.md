```
fit_mnf(raster::Union{<:AbstractRasterStack, <:AbstractRaster}, noise_covariance::Matrix; stats_fraction=1.0)
fit_mnf(signatures::Matrix, noise_covariance::Matrix; stats_fraction=1.0)
```

最小ノイズ分数（MNF）変換を指定された `AbstractRasterStack` または `AbstractRaster` に適合させます。

# パラメータ

  * `raster`: MNF 変換を適合させる `AbstractRaster` または `AbstractRasterStack`。
  * `signatures`: n x b 行列のスペクトル署名で、n は署名の数、b はバンドの数です。
  * `noise_sample`: ノイズ共分散行列を計算するために `raster` から抽出された均質（スペクトル的に均一）な領域。
  * `smooth`: `noise_sample` のいずれかのバンドにゼロ分散がある場合、MNF 変換を計算できません。これを修正するために、小さなスムージング項を導入することをお勧めします（デフォルトで真）。
