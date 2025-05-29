```
crop(x; to, touches=false, atol=0, [geometrycolumn])
crop(xs...; to)
```

1つまたは複数の [`AbstractRaster`](@ref) または [`AbstractRasterStack`](@ref) `x` を、オブジェクト `to` のサイズに合わせて切り取るか、共有されている任意の次元の最小値に合わせます。

`crop` は遅延評価であり、新しいメモリを割り当てるのではなく、オブジェクトへの `view` を使用します。

# キーワード

  * `to`: 切り取る対象のオブジェクト。これは [`Raster`](@ref) であるか、1つまたは複数のジオメトリである可能性があります。ジオメトリは、GeoInterface.jl の `AbstractGeometry`、`AbstractGeometry` のネストされた `Vector`、または `:geometry` 列またはポイントと値の列を含む Tables.jl 互換オブジェクトである場合、`geometrycolumn` を指定する必要があります。`to` キーワードが渡されない場合、すべての `xs` の最小共有領域が使用されます。
  * `touches`: `true` または `false`。オブジェクトの範囲に `Touches` ラッパーを使用するかどうか。例えば、ゾーン統計にラインを含める必要がある場合は、`true` を使用する必要があります。
  * `atol`: 範囲に切り取る際に使用する絶対許容誤差。エッジが `to` の範囲から `atol` 未満の場合、それらは含まれます。
  * `geometrycolumn`: `data` が Tables.jl 互換のテーブルである場合にジオメトリが含まれている列を手動で選択するための `Symbol`、またはポイント座標の列のための `Symbol` のタプル。

`crop` は遅延評価であるため、`filename` および `suffix` キーワードは使用されません。

# 例

別のラスタに切り取る:

```jldoctest
using Rasters, RasterDataSources, Plots
evenness = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)
rnge = Raster(EarthEnv{HabitatHeterogeneity}, :range)

# おおよそニュージーランドを evenness ラスタから切り取る
nz_bounds = X(165 .. 180), Y(-50 .. -32)
nz_evenness = evenness[nz_bounds...]

# evenness に合わせて範囲を切り取る
nz_range = crop(rnge; to=nz_evenness)
plot(nz_range)

savefig("build/nz_crop_example.png");
nothing

# 出力
```

![new zealand evenness cropped](nz_crop_example.png)

ポリゴンに切り取る:

```jldoctest
using Rasters, RasterDataSources, Plots, Dates, Shapefile, Downloads

# 国境のシェープファイルをダウンロード
shapefile_url = "https://github.com/nvkelso/natural-earth-vector/raw/master/10m_cultural/ne_10m_admin_0_countries.shp"
shapefile_name = "boundary.shp"
isfile(shapefile_name) || Downloads.download(shapefile_url, shapefile_name)
shp = Shapefile.Handle(shapefile_name).shapes[6]

evenness = Raster(EarthEnv{HabitatHeterogeneity}, :evenness)
argentina_evenness = crop(evenness; to=shp)
plot(argentina_evenness)

savefig("build/argentina_crop_example.png"); nothing

# 出力
```

![argentina evenness cropped](argentina_crop_example.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHub に問題を報告してください。
