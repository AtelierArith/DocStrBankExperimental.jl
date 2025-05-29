```
Raster <: AbstractRaster

Raster(filepath::String; kw...)
Raster(A::AbstractDimArray; kw...)
Raster(A::AbstractArray, dims; kw...)
```

空間/ラスタ配列データの一般的な [`AbstractRaster`](@ref) です。メモリバックの配列を保持することも、`lazy=true` の場合は、開いていないファイルへの `String` パスを保存する [`FileArray`](@ref) を保持することもできます。

`lazy=true` の場合、ファイルは `getindex` でインデックスを付けるか、`read(A)` が呼び出されたときにのみ遅延的に開かれます。ブロードキャスティング、ビューの取得、反転、その他のほとんどのメソッドはディスクからデータを*ロードしません*。これらは後で遅延的に適用されます。

# 引数

  * `dims`: `AbstractArray` が使用されるときに必要な `Dimension` の `Tuple`。

# キーワード

  * `name`: 配列のための `Symbol` 名で、`Raster` が NetCDF のようなマルチレイヤーファイルで使用されるときに、アルファベット順で最初の名前付きレイヤーを取得します。代わりに `RasterStack` を使用してマルチレイヤーファイルを読み込む場合、デフォルトではすべての変数がスタックに追加されます。
  * `group`: `name` が見つかるデータセット内のグループ。ネストされたデータセットにのみ必要です。`String` または `Symbol` は単一のグループを選択します。ペアを使用して、任意のネストされた深さでグループにアクセスすることもできます。すなわち `group=:group1 => :group2 => :group3`。
  * `missingval`: 通常ファイルから検出される欠損データを表す値。値が指定されていないか不正確であることがわかっている場合は手動で設定します。これはラスタ内の値を*変更しません*。単にどの値が欠損として扱われるかを割り当てるだけです。ラスタ内のすべての欠損値を置き換えるには、[`replace_missing`](@ref) を使用します。
  * `metadata`: 配列のための `Dict` または `Metadata` オブジェクト、または `NoMetadata()`。
  * `crs`: オブジェクトの `XDim`/`YDim` 次元の座標参照系。検出された crs が不正確であることがわかっている場合、またはファイルに存在しない場合のみこれを設定します。`crs` は GeoFormatTypes.jl の `CRS` または `Mixed` モードの `GeoFormat` オブジェクト、例えば `EPSG(4326)` であることが期待されます。
  * `mappedcrs`: オブジェクトの `XDim`/`YDim` 次元のマッピングされた座標参照系。`Mapped` ルックアップの場合、これらはインデックスの実際の値です。`Projected` ルックアップの場合、例えば `EPSG(4326)` の緯度/経度値でインデックスを付けるために使用でき、自動的に変換されます。検出された `mappedcrs` が不正確である場合、またはファイルに `mappedcrs` がない場合（例：tiff）のみこれを設定します。`mappedcrs` は GeoFormatTypes.jl の `CRS` または `Mixed` モードの `GeoFormat` 型であることが期待されます。
  * `refdims`: 配列がスライスされた位置 `Dimension` の `Tuple` で、デフォルトは `()` です。通常は必要ありません。

ファイルパス `String` が使用される場合：

  * `dropband`: ファイル名からスタックを作成する際に単一バンド次元を削除します。デフォルトは `true` です。
  * `lazy`: ディスクからデータを遅延的にロードするかどうかを指定する `Bool`。デフォルトは `false` です。
  * `replace_missing`: `missingval` を `missing` で置き換えます。`lazy=true` の場合、これは遅延的に行われます。現在、NetCDF および GRIB ファイルに対して `replace_missing` は常に true です。将来的には `replace_missing=false` もこれらのデータソースで機能するようになります。
  * `source`: 通常、ファイルパスの拡張子から自動的に検出されます。手動で強制するには、`Symbol` を渡すことができます `:gdal`, `:netcdf`, `:grd`, `:grib`。内部の [`Rasters.Source`](@ref) オブジェクト、例えば `Rasters.GDALsource()`、`Rasters.GRIBsource()` または `Rasters.NCDsource()` も使用できます。
  * `write`: Raster に対して `open` を呼び出すときのデフォルトの `write` キーワード値を定義します。デフォルトは `false` です。`lazy=true` の場合にのみ使用する意味があります。

A が `AbstractDimArray` の場合：

  * `data`: 既存の `AbstractRaster` のデータを置き換えることができます。
