```
RasterStack <: AbstrackRasterStack

RasterStack(data...; name, kw...)
RasterStack(data::Union{Vector,Tuple}; name, kw...)
RasterStack(data::NamedTuple; kw...)
RasterStack(s::AbstractRasterStack; kw...)
RasterStack(s::AbstractRaster; layersfrom=Band, kw...)
RasterStack(filename::AbstractString; kw...)
```

ファイルパスまたはパスの`NamedTuple`を`RasterStack`としてロードするか、引数、`Raster`の`Vector`または`NamedTuple`を`RasterStack`に変換します。

# 引数

  * `data`: [`Raster`](@ref)の`NamedTuple`、または`Vector`、`Tuple`またはスプラット引数の[`Raster`](@ref)。後者のオプションは`name`キーワード引数を渡す必要があります。
  * `filename`: スタックとしてロードされるファイル（netcdfやtifなど）または複数のファイルを含むディレクトリパス。

# キーワード

  * `name`: `Tuple`、`Vector`または`Raster`のスプラットが渡されたときにスタックレイヤー名として使用されます。`NameTuple`が使用される場合は効果がありません - `NamedTuple`のキーがレイヤー名になります。
  * `metadata`: `Dict`または`DimensionalData.Metadata`オブジェクト。
  * `refdims`: スタックがスライスされた`Dimension`の`Tuple`。
  * `layersfrom`: ファイルがすでにマルチレイヤーでない場合にスタックレイヤーをソースする`Dimension`。デフォルトは`nothing`で、単一の`RasterStack(raster)`は単一レイヤーのスタックになります。`RasterStack(raster; layersfrom=Band)`はバンドをレイヤーとして使用します。
  * `lazy`: スタックをディスクから遅延ロードするかどうかを指定する`Bool`。デフォルトは`false`です。
  * `dropband`: ファイル名からスタックを作成する際に単一バンド次元を削除します。デフォルトは`true`です。

```julia
files = (temp="temp.tif", pressure="pressure.tif", relhum="relhum.tif")
stack = RasterStack(files; mappedcrs=EPSG(4326))
stack[:relhum][Lat(Contains(-37), Lon(Contains(144))
```
