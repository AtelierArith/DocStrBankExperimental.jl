```
plot_signatures!(ax, bandset::Type{<:AbstractSatellite}, sigs; kwargs...)
plot_signatures!(ax, bandset::Vector{<:Pair}, sigs; colors=Makie.wong_colors(), label=:label)
```

既存の `Makie.Axis` に1つ以上の土地被覆タイプのスペクトル署名をプロットします。

# パラメータ

  * `ax`: 署名をプロットする `Makie.Axis`。
  * `bandset`: `AbstractSatellite` またはソートされた `band => wavelength` ペアのベクトル。
  * `sigs`: スペクトル署名とそれに関連するラベルからなる行を持つテーブル。

# キーワード

  * `label`: `sigs` に含まれる署名ラベルの列（デフォルト = `:label`）。
  * `colors`: プロットに使用されるカラースキーム（デフォルト = `Makie.wong_colors()`）。

# 例

```julia
using RemoteSensingToolbox, Rasters, GeoDataFrames, Statistics, CairoMakie

# 画像を読み込み、DNを反射率に変換
landsat = Landsat8("data/LC08_L2SP_043024_20200802_20200914_02_T1/")
sentinel = Sentinel2{20}("data/T11UPT_20200804T183919/")
landsat_reflectance = decode(Landsat8, RasterStack(landsat))
sentinel_reflectance = decode(Sentinel2, RasterStack(sentinel))

# シェープファイルから土地被覆ラベルを読み込む
shp = GeoDataFrames.read("data/landcover/landcover.shp")

# 各土地被覆タイプの平均スペクトル署名を抽出
landsat_sigs = extract_signatures(mean, landsat_reflectance, shp, :MC_name)
sentinel_sigs = extract_signatures(mean, sentinel_reflectance, shp, :MC_name)

# 図と軸を作成
fig = Figure(resolution=(800,550));
ax1 = Axis(fig[1,1], ylabel="反射率", title="Landsat署名")
ax2 = Axis(fig[2,1], xlabel="波長 (nm)", ylabel="反射率", title="Sentinel署名")

# 署名をプロット
plot_signatures!(ax1, Landsat8, landsat_sigs, colors=[:brown, :orange, :blue, :green])
plot_signatures!(ax2, Sentinel2{20}, sentinel_sigs, colors=[:brown, :orange, :blue, :green])

# 凡例を追加
Legend(fig[:,2], ax1)
```
