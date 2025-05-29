```
missingmask(obj::Raster; kw...)
missingmask(obj; [to, res, size])
missingmask(obj::RasterStack; alllayers=true, kw...)
```

別の `Raster` から `missing` と `true` の値のマスク配列を作成します。 `AbstractRasterStack` または `AbstractRasterSeries` も受け入れられます。

[`AbstractRaster`](@ref) のデフォルトの `missingval` は `missingval(A)` ですが、他の値を手動で選択することもできます。

`AbstractRaster` に対して `missingmask` を呼び出すと返される配列は、元の配列と同じサイズとフィールドを持つ [`Raster`](@ref) です。

# 引数

  * `obj`: [`Raster`](@ref) または1つ以上のジオメトリ。ジオメトリは、GeoInterface.jl の `AbstractGeometry`、`AbstractGeometry` のネストされた `Vector`、または `:geometry` 列またはポイントと値の列を含む Tables.jl 互換オブジェクトである場合、`geometrycolumn` を指定する必要があります。

# キーワード

  * `alllayers`: `true` の場合、すべてのレイヤーのマスクが取得され、それ以外の場合は最初のレイヤーのみが使用されます。デフォルトは `true` です。
  * `invert`: マスクを反転させ、`with` で欠損していない領域がマスクされ、`with` で欠損している領域がマスクされます。
  * `to`: `Raster`、`RasterStack`、`Dimension` または `Extents.Extent` の `Tuple`。`to` オブジェクトが提供されない場合、範囲はジオメトリから計算されます。さらに、`to` オブジェクトまたは `Extent` が `to` に渡されない場合、`size` または `res` キーワードも使用する必要があります。
  * `res`: 次元の解像度（通常はメートルまたは度）、`Real` または `Tuple{<:Real,<:Real}`。`to` が使用されない場合または `Extents.Extent` であり、`size` が使用されない場合にのみ必要です。
  * `size`: 出力配列のサイズ、`Tuple{Int,Int}` または正方形のための単一の `Int`。`to` が使用されない場合または `Extents.Extent` であり、`res` が使用されない場合にのみ必要です。
  * `crs`: `to` が渡されない場合または `Extent` の場合に結果のラスタに添付される `crs`。それ以外の場合は `to` からの crs が使用されます。
  * `boundary`: ポリゴンの場合、`:center` がポリゴン内にあるピクセル、ポリゴンがピクセルに `touches` している場所、またはポリゴンの完全に `:inside` にある場所を含めます。デフォルトは `:center` です。
  * `shape`: `data` を `:polygon`、`:line` または `:point` ジオメトリとして扱うよう強制します。ポイントやラインをポリゴンとして使用すると、予期しない結果が生じる可能性があります。
  * `geometrycolumn`: `data` が Tables.jl 互換のテーブルである場合にジオメトリが含まれている列を手動で選択するための `Symbol`、またはポイント座標の列のための `Symbol` のタプル。

# 例

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates
wc = Raster(WorldClim{Climate}, :prec; month=1)
missingmask(wc) |> plot

savefig("build/missingmask_example.png"); nothing

# output
```

![missingmask](missingmask_example.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、github に問題を報告してください。
