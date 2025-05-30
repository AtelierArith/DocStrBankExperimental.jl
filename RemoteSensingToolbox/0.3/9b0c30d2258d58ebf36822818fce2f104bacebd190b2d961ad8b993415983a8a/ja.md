```
true_color(src::AbstractSatellite; lower=0.02, upper=0.98)
true_color(s::Type{AbstractSatellite}, raster::AbstractRasterStack; lower=0.02, upper=0.98)
```

衛星画像を真の色のバンドの組み合わせを使用して視覚化します。これは自然な画像のように見えます。

`AbstractSatellite` または `Type{AbstractSatellite}` と `AbstractRasterStack` の組み合わせのいずれかを受け入れます。

`RGB{N0f8}` または `Gray{N0f8}` 要素の `Array` を返します。

# キーワード

  * `lower`: 画像のヒストグラムを調整するために使用する下位パーセンタイル。
  * `upper`: 画像のヒストグラムを調整するために使用する上位パーセンタイル。

# 例

```julia
using RemoteSensingToolbox, Rasters

# Landsat 8 画像を準備
src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1")

# ディスクからバンドを直接読み込む
true_color(src; upper=0.90)

# RasterStackからバンドを読み込む
stack = RasterStack(src; lazy=true)
true_color(Landsat8, stack; upper=0.90)
```
