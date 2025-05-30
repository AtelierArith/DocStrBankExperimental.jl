```
plot_signatures(bandset::Type{<:AbstractSatellite}, sigs; kwargs...)
plot_signatures(bandset::Vector{<:Pair}, sigs; colors=Makie.wong_colors(), label=:label)
```

1つ以上の土地被覆タイプのスペクトル署名をプロットします。

# パラメータ

  * `bandset`: `AbstractSatellite` またはソートされた `band => wavelength` ペアのベクター。
  * `sigs`: スペクトル署名とそれに関連するラベルからなる行を持つテーブル。

# キーワード

  * `label`: `sigs` 内の署名ラベルを含む列（デフォルト = `:label`）。
  * `colors`: プロットで使用されるカラースキーム（デフォルト = `Makie.wong_colors()`）。

# 例

```julia
julia> src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1");

julia> surface_reflectance = decode(Landsat8, RasterStack(src));

julia> shp = GeoDataFrames.read("data/landcover/landcover.shp");

julia> sigs = extract_signatures(mean, surface_reflectance, shp, :MC_name);

julia> plot_signatures(Landsat8, sigs, colors=[:brown, :orange, :blue, :green])
```
