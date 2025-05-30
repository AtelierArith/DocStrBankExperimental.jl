```
estimate_noise(raster::Union{<:AbstractRaster, <:AbstractRasterStack}; smooth=false)
```

与えられたラスタのノイズ共分散行列を推定します。

[Switzer and Green](https://www.researchgate.net/publication/239665649_MinMax_Autocorrelation_factors_for_multivariate_spatial_imagery_Technical_Report_6)によって提案された最小/最大自己相関因子を使用します。

最良の結果を得るためには、提供されたラスタはスペクトル的に均質であるべきです（例：開けた野原や水域）。

# パラメータ

  * `raster`: `AbstractRaster`または`AbstractRasterStack`。
  * `smooth`: 数値的安定性のために、バンドの分散がゼロであってはなりません。この条件を満たすためにスムージング項を適用できます。

# 例

```julia
using RemoteSensingToolbox, Rasters

# データをロード
src = DESIS("DESIS-HSI-L2A-DT0485529167_001-20220712T223540-V0220")
desis = decode(DESIS, Raster(src, :Bands))

# 均質な関心領域を抽出
roi = desis[X(1019:1040), Y(550:590)]

# ノイズを推定
ncm = estimate_noise(roi, smooth=true)
```
