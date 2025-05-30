```
Raster <: AbsractRaster

Raster(filepath::AbstractString, dims; kw...)
Raster(A::AbstractArray{T,N}, dims; kw...)
Raster(A::AbstractRaster; kw...)
```

空間/ラスタ配列データのための一般的な [`AbstractRaster`](@ref) です。これは、メモリバックの配列または [`FileArray`](@ref) を保持することができ、これは単に未オープンのファイルへの `String` パスを保持します。これは、`getindex` でインデックスを付けるか、`read(A)` が呼び出されたときに遅延的にのみオープンされます。ブロードキャスティング、ビューの取得、反転、およびほとんどの他のメソッドは *ディスクから* データをロードしません：それらは後で遅延的に適用されます。

# キーワード

  * `dims`: 配列の `Dimension` の `Tuple`。
  * `lazy`: ディスクからスタックを遅延的にロードするかどうかを指定する `Bool`。デフォルトは `false`。
  * `name`: 配列の `Symbol` 名、これは `Raster` が NetCDF のようなマルチレイヤーファイルで使用されるときに名前付きレイヤーを取得します。
  * `missingval`: 通常ファイルから検出される欠損データを表す値。値が指定されていないか不正確であることがわかっている場合に手動で設定します。これはラスタ内の値を *変更* することはなく、単に欠損として扱われる値を割り当てます。ラスタ内のすべての欠損値を置き換えるには、[`replace_missing`](@ref) を使用します。
  * `metadata`: 配列のための `ArrayMetadata` オブジェクト、または `NoMetadata()`。
  * `crs`: オブジェクトの `XDim`/`YDim` 次元の座標参照系。検出された crs が不正確であることがわかっている場合、またはファイルに存在しない場合にのみこれを設定します。`crs` は GeoFormatTypes.jl の `CRS` または `Mixed` `GeoFormat` タイプであることが期待されます。
  * `mappedcrs`: オブジェクトの `XDim`/`YDim` 次元のマッピングされた座標参照系。`Mapped` ルックアップの場合、これらはインデックスの実際の値です。`Projected` ルックアップの場合、これは例えば `EPSG(4326)` 緯度/経度値でインデックスを付けるために使用でき、自動的に変換されます。検出された `mappedcrs` が不正確である場合、またはファイルに `mappedcrs` がない場合（例：tiff）のみこれを設定します。`mappedcrs` は GeoFormatTypes.jl の `CRS` または `Mixed` `GeoFormat` タイプであることが期待されます。
  * `dropband`: 単一バンド次元を削除します。デフォルトは `true`。

# 内部キーワード

場合によっては、これらのキーワードを設定することも可能です。

  * `data`: `AbstractRaster` 内のデータを置き換えることができます。
  * `refdims`: 配列がスライスされた位置の `Dimension` の `Tuple`、デフォルトは `()`。

```
