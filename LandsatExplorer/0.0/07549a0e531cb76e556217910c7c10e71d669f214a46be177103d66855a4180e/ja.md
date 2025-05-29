```
search(satellite, level; dates=nothing, clouds=nothing, geom=nothing, max_results=100)
```

指定された衛星と処理レベルに属するLandsatシーンを検索します。

# パラメータ

  * `satellite`: `"LANDSAT_5"`、`"LANDSAT_7"`、`"LANDSAT_8"`、または`"LANDSAT_9"`のいずれか。
  * `level`: 処理レベル; 1または2のいずれか。

# キーワード

  * `dates`: 画像取得のための日付範囲。`DateTime`オブジェクトのタプルである必要があります。
  * `clouds`: 許容される最大雲量（パーセンテージ）。
  * `geom`: 興味のある地域を指定するジオメトリ。`Point`、`BoundingBox`、または他の`GeoInterface`互換のジオメトリであることができます。
  * `max_results`: 戻り値の最大数（デフォルト = 100）。

# 戻り値

`:Name`、`:AcquisitionDate`、`:PublicationDate`、`:CloudCover`、および`:Id`の列を持つ`DataFrame`。

# 例

```julia
julia> p = Point(52.0, -114.2);

julia> dates = (DateTime(2020, 8, 1), DateTime(2020, 9, 1));

julia> search("LANDSAT_8", 2, dates=dates, geom=p, clouds=21)
3×5 DataFrame
 Row │ Name                               AcquisitionDate      Pub ⋯
     │ String                             String               Str ⋯
─────┼──────────────────────────────────────────────────────────────
   1 │ LC08_L2SP_043024_20200818_202008…  2020-08-18 00:00:00  202 ⋯
   2 │ LC08_L2SP_042024_20200811_202009…  2020-08-11 00:00:00  202
   3 │ LC08_L2SP_043024_20200802_202009…  2020-08-02 00:00:00  202
                                                   3 columns omitted
```
