```
zonal(f, x::Union{Raster,RasterStack}; of, kw...)
```

`of`オブジェクト/sによってカバーされる`Raster`または`RasterStack`のゾーンのゾーン統計を計算します。

# 引数

  * `f`: `sum`や`Statistics.mean`のように、反復可能なものを単一の値に減少させる任意の関数
  * `x`: `Raster`または`RasterStack`
  * `of`: `DimTuple`、`Extent`、[`Raster`](@ref)または1つ以上のジオメトリ。ジオメトリは、GeoInterface.jlの`AbstractGeometry`、`AbstractGeometry`のネストされた`Vector`、または`:geometry`列またはポイントと値の列を含むTables.jl互換オブジェクトである場合、`geometrycolumn`を指定する必要があります。

# キーワード

  * `geometrycolumn`: `data`がTables.jl互換のテーブルである場合、ジオメトリが含まれる列を手動で選択するための`Symbol`、またはポイント座標の列のための`Symbol`のタプル。

これらは、`of`がGeoInterface.jl互換のオブジェクトである場合に使用できます：

  * `shape`: 可能な場合、`data`を`:polygon`、`:line`または`:point`として扱うよう強制します。
  * `boundary`: ポリゴンの場合、`:center`がポリゴン内にあるピクセル、線がピクセルに`touches`する場合、またはポリゴン内に完全に`inside`であるピクセルを含めます。デフォルトは`:center`です。
  * `progress`: 進行状況バーを表示します。デフォルトは`true`、`false`で非表示にします。
  * `skipmissing`: `skipmissing(A)`の結果に`f`を適用するかどうか。`true`の場合、`f`には値のイテレータが渡され、すべての空間情報が失われます。`false`の場合、`f`にはマスクされた`Raster`または`RasterStack`が渡され、欠損値の処理を自分で行う必要があります。デフォルト値は`true`です。

# 例

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, DataFrames, Statistics, Dates, NaturalEarth
# 国境をダウンロード
countries = naturalearth("admin_0_countries", 10) |> DataFrame
# WorldClimからラスタースタックをダウンロードして読み込む
st = RasterStack(WorldClim{Climate}; month=Jan)
# すべての国の気候変数の1月の平均を計算
january_stats = zonal(mean, st; of=countries, boundary=:touches, progress=false) |> DataFrame
# 国名列を追加（natural earthにはいくつかの文字列エラーがあるようです）
insertcols!(january_stats, 1, :country => first.(split.(countries.ADMIN, r"[^A-Za-z ]")))
# 出力
258×8 DataFrame
 Row │ country                       tmin       tmax       tavg       prec     ⋯
     │ SubStrin…                     Float32    Float32    Float32    Float64  ⋯
─────┼──────────────────────────────────────────────────────────────────────────
   1 │ Indonesia                      21.5447    29.1865    25.3656   271.063  ⋯
   2 │ Malaysia                       21.3087    28.4291    24.8688   273.381
   3 │ Chile                           7.24534   17.9262    12.5858    78.1287
   4 │ Bolivia                        17.2065    27.7454    22.4758   192.542
   5 │ Peru                           15.0273    25.5504    20.2889   180.007  ⋯
   6 │ Argentina                      13.6751    27.6716    20.6732    67.1837
   7 │ Dhekelia Sovereign Base Area    5.87126   15.8991    10.8868    76.25
   8 │ Cyprus                          5.65921   14.6665    10.1622    97.4474
  ⋮  │              ⋮                    ⋮          ⋮          ⋮         ⋮     ⋱
 252 │ Spratly Islands                25.0       29.2       27.05      70.5    ⋯
 253 │ Clipperton Island              21.5       33.2727    27.4        6.0
 254 │ Macao S                        11.6694    17.7288    14.6988    28.0
 255 │ Ashmore and Cartier Islands   NaN        NaN        NaN        NaN
 256 │ Bajo Nuevo Bank               NaN        NaN        NaN        NaN      ⋯
 257 │ Serranilla Bank               NaN        NaN        NaN        NaN
 258 │ Scarborough Reef              NaN        NaN        NaN        NaN
                                                  3 columns and 243 rows omitted
```
