```
boolmask(obj::Raster; [missingval])
boolmask(obj; [to, res, size])
boolmask(obj::RasterStack; alllayers=true, kw...)
```

別の `Raster` から `Bool` 値のマスク配列を作成します。 `AbstractRasterStack` または `AbstractRasterSeries` も受け付けます。

`AbstractRaster` に対して `boolmask` を呼び出すと返される配列は、元の配列と同じ次元を持ち、`missingval` は `false` です。

# 引数

  * [`Raster`](@ref) または1つ以上のジオメトリ。ジオメトリは、GeoInterface.jl の `AbstractGeometry`、ネストされた `Vector` の `AbstractGeometry`、または `:geometry` 列またはポイントと値の列を含む Tables.jl 互換オブジェクトである場合、`geometrycolumn` を指定する必要があります。

# `Raster` / `RasterStack` キーワード

  * `invert`: マスクを反転させ、`with` に欠損がない領域をマスクし、`with` に欠損がある領域をマスクします。
  * `missingval`: ソース配列の欠損値で、デフォルトは `missingval(raster)` です。

# キーワード

  * `alllayers`: `true` の場合、すべてのレイヤーのマスクが取得され、それ以外の場合は最初のレイヤーのみが使用されます。デフォルトは `true` です。
  * `to`: `Raster`、`RasterStack`、`Tuple` の `Dimension` または `Extents.Extent`。`to` オブジェクトが提供されない場合、範囲はジオメトリから計算されます。さらに、`to` オブジェクトまたは `Extent` が `to` に渡されない場合、`size` または `res` キーワードも使用する必要があります。
  * `res`: 次元の解像度（通常はメートルまたは度）、`Real` または `Tuple{<:Real,<:Real}`。`to` が使用されない場合または `Extents.Extent` であり、`size` が使用されない場合にのみ必要です。
  * `size`: 出力配列のサイズ、`Tuple{Int,Int}` または正方形の単一の `Int` として。`to` が使用されない場合または `Extents.Extent` であり、`res` が使用されない場合にのみ必要です。
  * `crs`: `to` が渡されない場合または `Extent` の場合に結果のラスタに添付される `crs`。それ以外の場合は `to` からの crs が使用されます。
  * `boundary`: ポリゴンの場合、`：center` がポリゴン内にあるピクセル、ポリゴンがピクセルに `：touches` している場合、またはポリゴンの完全に `：inside` にあるピクセルを含めます。デフォルトは `：center` です。
  * `shape`: `data` を `：polygon`、`：line` または `：point` ジオメトリとして扱うよう強制します。ポイントやラインをポリゴンとして使用すると、予期しない結果が生じる可能性があります。
  * `geometrycolumn`: `data` が Tables.jl 互換のテーブルである場合、ジオメトリが含まれている列を手動で選択するための `Symbol`、またはポイント座標の列のための `Symbol` のタプル。
  * `threaded`: 操作を並列で実行します。デフォルトは `false` です。特定の状況では、`threaded` は単一スレッドの操作に対して大きな速度向上をもたらすことがあります。これは、低解像度のラスタに書き込まれた複雑なジオメトリに当てはまることがありますが、高解像度のラスタに対して単純なジオメトリには当てはまらないかもしれません。非常に大きなラスタでは、スレッド処理が過剰なメモリ使用のために逆効果になる可能性があります。注意が必要です：`threaded` は、`BitArray` や競合条件が発生する可能性のある他の配列に書き込むインプレース関数では使用しないでください。
  * `progress`: 進行状況バーを表示します。デフォルトは `true` で、`false` にすると非表示になります。

表形式のデータ、フィーチャコレクション、およびその他の反復可能なものについて

  * `collapse`: `true` の場合、すべてのジオメトリマスクを単一のマスクに統合します。そうでない場合、追加の `geometry` 次元を持つ Raster を返します。この軸に沿った各スライスは、テーブルの各行の `geometry` オブジェクト、フィーチャコレクションのフィーチャ、または反復可能な各ジオメトリのマスクになります。

# 例

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots, Dates
wc = Raster(WorldClim{Climate}, :prec; month=1)
boolmask(wc) |> plot

savefig("build/boolmask_example.png"); nothing

# output
```

![boolmask](boolmask_example.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、github に問題を報告してください。 ```
