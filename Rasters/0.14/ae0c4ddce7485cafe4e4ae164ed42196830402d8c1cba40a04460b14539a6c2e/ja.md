```
RasterSeries <: AbstractRasterSeries

RasterSeries(rasters::AbstractArray{<:AbstractRaster}, dims; [refdims])
RasterSeries(stacks::AbstractArray{<:AbstractRasterStack}, dims; [refdims]) 

RasterSeries(paths::AbstractArray{<:AbstractString}, dims; child, duplicate_first, kw...)
RasterSeries(path:::AbstractString, dims; ext, separator, child, duplicate_first, kw...)

RasterSeries(objects::AbstractBasicDimArray; kw...)
```

[`AbstractRasterSeries`](@ref) の具体的な実装です。

`RasterSeries` は、ある次元に沿った `Raster` または `RasterStack` の配列です。

既存の `Raster` または `RasterStack` は `RasterSeries` にラップすることができ、新しいファイルは `String` の配列または単一の `String` から読み込むことができます。

単一の `String` は、ディレクトリ全体を指すことも、共通の幹を共有するディレクトリ内のファイルのシリーズの名前を指すこともできます。ファイル名の違いはシリーズのルックアップに使用できます。

例えば、以下のパスにあるいくつかの tifs を使って：

```
"series_dir/myseries_2001-01-01T00:00:00.tif"
"series_dir/myseries_2002-01-01T00:00:00.tif"
```

`DateTime` ルックアップを使用して `RasterSeries` を読み込むことができます：

```julia
julia> ser = RasterSeries("series_dir/myseries.tif", Ti(DateTime))
2-element RasterSeries{Raster,1} with dimensions: 
  Ti Sampled{DateTime} DateTime[DateTime("2001-01-01T00:00:00"), DateTime("2002-01-01T00:00:00")] ForwardOrdered Irregular Points
```

`DateTime` サフィックスはファイル名から解析されます。`Ti(Int)` を使用すると、代わりに整数を解析しようとします。

ディレクトリを使用するだけでも機能しますが、他のファイルが混在している場合は注意が必要です：

```julia
julia> ser = RasterSeries("series_dir", Ti(DateTime))
2-element RasterSeries{Raster,1} with dimensions: 
  Ti Sampled{DateTime} DateTime[DateTime("2001-01-01T00:00:00"), DateTime("2002-01-01T00:00:00")] ForwardOrdered Irregular Points
```

# 引数

  * `dims`: シリーズの次元。

# キーワード

文字列のパスのベクターまたは単一の文字列パスからシリーズを読み込むとき：

  * `child`: ファイル名が渡されたときに使用する子オブジェクトのコンストラクタ。`Raster` または `RasterStack` であることができます。デフォルトは `Raster` です。
  * `duplicate_first::Bool`: 最初のファイルの次元とメタデータを他のすべてのファイルと重複させるかどうか。次元が同じ大きなシリーズでは、読み込み時間を節約できます。デフォルトは `false` です。
  * `lazy`: ディスクからデータを遅延読み込みするかどうかを指定する `Bool`。デフォルトは `false` です。
  * `kw`: 子コンストラクタ [`Raster`](@ref) または [`RasterStack`](@ref) に渡されるキーワード。

単一の `String` パスからシリーズを読み込むとき：

  * `separator`: ファイル名の残りの部分からルックアップ要素を分割するために使用されるセパレーター。デフォルトは '_' です。

その他：

  * `refdims`: 既存の参照次元、通常は必要ありません。
