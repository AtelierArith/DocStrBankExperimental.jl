```
RasterStack <: AbstrackRasterStack

RasterStack(data...; name, kw...)
RasterStack(data::Union{Vector,Tuple}; name, kw...)
RasterStack(data::NamedTuple; kw...))
RasterStack(data::RasterStack; kw...)
RasterStack(data::Raster; layersfrom=Band, kw...)
RasterStack(filepath::AbstractString; kw...)
```

ファイルパスまたはパスの`NamedTuple`を`RasterStack`としてロードするか、引数、`Vector`または`Raster`の`NamedTuple`を`RasterStack`に変換します。

# 引数

  * `data`: [`Raster`](@ref)sの`NamedTuple`または`String`、または`Vector`、`Tuple`またはスプラット引数の[`Raster`](@ref)。後者のオプションは`name`キーワード引数を渡す必要があります。
  * `filepath`: スタックとしてロードされるファイル（netcdfやtifなど）または複数のファイルを含むディレクトリパス。

# キーワード

  * `name`: `Tuple`、`Vector`または`Raster`のスプラットが渡されたときにスタックレイヤー名として使用されます。`NameTuple`が使用される場合は効果がありません - `NamedTuple`のキーがレイヤー名になります。
  * `group`: `name`が見つかるデータセット内のグループ。ネストされたデータセットにのみ必要です。`String`または`Symbol`は単一のグループを選択します。ペアを使用して、任意のネストされた深さでグループにアクセスすることもできます。すなわち、`group=:group1 => :group2 => :group3`。
  * `metadata`: `Dict`または`DimensionalData.Metadata`オブジェクト。
  * `missingval`: 欠損データを表す値で、通常はファイルから検出され、自動的に`missing`に変換されます。`0`や`NaN`などの代替値に設定することは、パフォーマンス向上のために望ましい場合があります。`nothing`は欠損値を指定しません。同じ`missingval`を使用すると、ファイルがすでに持っている値の置き換えのオーバーヘッドが削除されます。これは、`missingval`関数を`missingval`として渡すことで行うことができます。ファイルに不正な値がある場合、`correct_value => missing`や`correct_value => NaN`のようにペアとして変換を手動で定義できます。`correct_value => correct_value`は変更のオーバーヘッドを削除します。注意: `raw=true`が設定されている場合、`missingval`はファイルに指定された値から変更されません。

    `RasterStack`の場合、レイヤーが異なる`missingval`を持つ必要がある場合は`NamedTuple`も渡すことができます。
  * `crs`: オブジェクトの`XDim`/`YDim`次元の座標参照系。検出されたcrsが不正であることがわかっている場合、またはファイルに存在しない場合のみこれを設定します。`crs`はGeoFormatTypes.jlの`CRS`または`Mixed`モードの`GeoFormat`オブジェクトであることが期待されます。例えば、`EPSG(4326)`のように。
  * `mappedcrs`: オブジェクトの`XDim`/`YDim`次元のマッピングされた座標参照系。`Mapped`ルックアップの場合、これらはインデックスの実際の値です。`Projected`ルックアップの場合、例えば`EPSG(4326)`の緯度/経度値にインデックスを付けるために使用でき、自動的に変換されます。検出された`mappedcrs`が不正である場合、またはファイルに`mappedcrs`がない場合（例えばtiff）、これを設定します。`mappedcrs`はGeoFormatTypes.jlの`CRS`または`Mixed`モードの`GeoFormat`型であることが期待されます。
  * `refdims`: スタックがスライスされた`Dimension`の`Tuple`。

1つまたは複数のファイルパスが使用される場合:

  * `dropband`: ファイル名からスタックを作成する際に単一バンド次元を削除します。デフォルトは`true`です。
  * `lazy`: ディスクからデータを遅延ロードするかどうかを指定する`Bool`。デフォルトは`false`です。
  * `raw`: すべてのスケーリングとマスキングをオフにし、ディスクから生の値をロードします。デフォルトは`false`です。`true`の場合、`scaled`は`false`に設定され、`missingval`はファイル内の既存の欠損値に設定されます。`scaled`または`missingval`が手動で別の値に設定されると警告が表示されます。
  * `scaled`: スケールとオフセットを`x * scale + offset`として適用します。ここで、`scale`および/または`offset`はファイルメタデータに見つかります。デフォルトは`true`です。これは、データがディスクスペースを節約するために例えばUInt8に変換されている場合によくあります。`scale`と`offset`のメタデータを無視するには、`scaled=false`を使用します。注意1: `scale`と`offset`が`1.0`と`0.0`の場合、それらは無視され、元の型が使用されます。たとえ`scaled=true`であっても、これらの値はフォールバックデフォルトである可能性があり、すべての`Real`配列をより大きな`Float64`値に変換したくないからです。注意2: `raw=true`は`scaled`と`missingval`を無視し、生の値を返します。
  * `source`: 通常、ファイルパスの拡張子から自動的に検出されます。手動で強制するには、`:gdal`、`:netcdf`、`:grd`、`:grib`の`Symbol`を渡すことができます。内部の[`Rasters.Source`](@ref)オブジェクト、例えば`Rasters.GDALsource()`、`Rasters.GRIBsource()`または`Rasters.NCDsource()`も使用できます。

単一の`Raster`が使用される場合:

  * `layersfrom`: ファイルがすでにマルチレイヤーでない場合にスタックレイヤーをソースする`Dimension`。デフォルトは`nothing`で、`RasterStack(raster)`は単一レイヤーのスタックになります。`RasterStack(raster; layersfrom=Band)`はバンドをレイヤーとして使用します。

```julia
files = (temp="temp.tif", pressure="pressure.tif", relhum="relhum.tif")
stack = RasterStack(files; mappedcrs=EPSG(4326))
stack[:relhum][Lat(Contains(-37), Lon(Contains(144))
```
