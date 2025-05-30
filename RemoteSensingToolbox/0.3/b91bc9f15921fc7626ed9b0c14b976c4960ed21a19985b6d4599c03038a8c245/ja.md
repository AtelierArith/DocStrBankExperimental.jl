```
visualize(g::AbstractRaster; lower=0.02, upper=0.98)
visualize(r::AbstractRaster, g::AbstractRaster, b::AbstractRaster; lower=0.02, upper=0.98)
```

RGBまたはグレースケールの衛星画像を視覚化します。

`RGB{N0f8}`または`Gray{N0f8}`要素の`Array`を返します。

# キーワード

  * `lower`: 画像のヒストグラムを調整するために使用する下位パーセンタイル。
  * `upper`: 画像のヒストグラムを調整するために使用する上位パーセンタイル。

# 例

```julia
using RemoteSensingToolbox, Rasters, FileIO

# Landsat 8画像を準備
src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1")

# 真の色画像を表示
r, g, b = RasterStack(src, [:red, :green, :blue])
img = visualize(r, g, b; upper=0.90)
FileIO.save("truecolor.jpg", img)
```
