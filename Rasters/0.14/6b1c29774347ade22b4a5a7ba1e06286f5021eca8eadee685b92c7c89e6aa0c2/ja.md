```
Raster <: AbstractRaster

Raster(filepath::String; kw...)
Raster(A::AbstractDimArray; kw...)
Raster(A::AbstractArray, dims; kw...)
```

空間/ラスタ配列データのための一般的な [`AbstractRaster`](@ref) です。メモリバックの配列を保持することも、`lazy=true` の場合は、未オープンのファイルへの `String` パスを保存する [`FileArray`](@ref) を保持することもできます。

`lazy=true` の場合、ファイルは `getindex` でインデックスを付けるか、`read(A)` が呼び出されたときにのみ遅延的にオープンされます。ブロードキャスティング、ビューの取得、反転、その他のほとんどのメソッドはディスクからデータを*ロードしません*。これらは後で遅延的に適用されます。

# 引数

  * `dims`: `AbstractArray` が使用されるときに必要な `Dimension` の `Tuple`。

# キーワード

  * `name`: ラスタのための `Symbol` 名で、`Raster` が NetCDF のようなマルチレイヤーのファイルで使用されるときに名前付きレイヤーを取得します。
  * `group`: `name` が見つかるデータセット内のグループ。ネストされたデータセットにのみ必要です。`String` または `Symbol` は単一のグループを選択します。ペアを使用して、任意のネストされた深さのグループにアクセスすることもできます。例: `group=:group1 => :group2 => :group3`。
  * `missingval`: 欠損データを表す値で、通常はファイルから検出され、自動的に `missing` に変換されます。`0` や `NaN` などの代替値に設定することは、パフォーマンス向上のために望ましい場合があります。`nothing` は欠損値がないことを指定します。同じ `missingval` を使用すると、置き換えのオーバーヘッドが削除されます。これは、`missingval` 関数を `missingval` として渡すことで行えます。ファイルに不正な値がある場合、`correct_value => missing` や `correct_value => NaN` のようにペアで変換を手動で定義できます。`correct_value => correct_value` は変更のオーバーヘッドを削除します。注意: `raw=true` が設定されている場合、`missingval` はファイルに指定された値から変更されません。
  * `metadata`: 配列のための `Dict` または `Metadata` オブジェクト、または `NoMetadata()`。
  * `crs`: オブジェクトの `XDim`/`YDim` 次元の座標参照系。検出された crs が不正であることがわかっている場合、またはファイルに存在しない場合のみ設定します。`crs` は GeoFormatTypes.jl の `CRS` または `Mixed` モードの `GeoFormat` オブジェクト、例えば `EPSG(4326)` であることが期待されます。
  * `mappedcrs`: オブジェクトの `XDim`/`YDim` 次元のマッピングされた座標参照系。`Mapped` ルックアップの場合、これらはインデックスの実際の値です。`Projected` ルックアップの場合、例えば `EPSG(4326)` の緯度/経度値でインデックスを付けるために使用でき、自動的に変換されます。検出された `mappedcrs` が不正である場合、またはファイルに `mappedcrs` がない場合（例: tiff）のみ設定します。`mappedcrs` は GeoFormatTypes.jl の `CRS` または `Mixed` モードの `GeoFormat` 型であることが期待されます。
  * `refdims`: 配列がスライスされた位置 `Dimension` の `Tuple` で、デフォルトは `()` です。通常は必要ありません。

ファイルパス `String` が使用される場合:

  * `dropband`: ファイル名からスタックを作成する際に単一バンドの次元を削除します。デフォルトは `true` です。
  * `lazy`: ディスクからデータを遅延的にロードするかどうかを指定する `Bool`。デフォルトは `false` です。
  * `source`: 通常はファイルパスの拡張子から自動的に検出されます。手動で強制するには、`Symbol` を渡すことができます: `:gdal`, `:netcdf`, `:grd`, `:grib`。内部の [`Rasters.Source`](@ref) オブジェクト、例えば `Rasters.GDALsource()`、`Rasters.GRIBsource()` または `Rasters.NCDsource()` も使用できます。
  * `scaled`: ファイルメタデータに見つかった `scale` および/または `offset` を使用して `x * scale + offset` としてスケールとオフセットを適用します。デフォルトは `true` です。これは、データがディスクスペースを節約するために例えば UInt8 に変換されている場合に一般的です。`scale` および `offset` メタデータを無視するには、`scaled=false` を使用します。注意 1: `scale` と `offset` が `1.0` と `0.0` の場合、それらは無視され、元の型が使用されます。これは、これらの値がフォールバックデフォルトであり、すべての `Real` 配列を大きな `Float64` 値に変換したくないためです。注意 2: `raw=true` は `scaled` と `missingval` を無視し、生の値を返します。
  * `raw`: すべてのスケーリングとマスキングをオフにし、ディスクから生の値をロードします。デフォルトは `false` です。`true` の場合、`scaled` は `false` に設定され、`missingval` はファイル内の既存の欠損値に設定されます。`scaled` または `missingval` が手動で別の値に設定されている場合、警告が表示されます。

A が `AbstractDimArray` の場合:

  * `data`: 既存の `AbstractRaster` のデータを置き換えることができます。

```
