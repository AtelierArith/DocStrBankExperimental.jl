```
search(satellite; product=nothing, dates=nothing, tile=nothing, clouds=nothing, geom=nothing, max_results=100)
```

提供されたフィルターに一致する衛星画像を検索します。

# パラメータ

  * `satellite`: "SENTINEL-1"、"SENTINEL-2"、または"SENTINEL-3"のいずれか。

# キーワード

  * `product`: "L2A"、"L1C"、"GRD"など、検索する製品タイプ。
  * `dates`: 画像取得のための日付範囲。`DateTime`オブジェクトのタプルである必要があります。
  * `tile`: 特定のタイルに結果を制限します。Sentinel-2のみで利用可能です。
  * `clouds`: 許容される最大雲量（パーセンテージ）。Sentinel-1では利用できません。
  * `geom`: 興味のある地域を指定するジオメトリ。`Point`、`BoundingBox`、または他の`GeoInterface`互換のジオメトリであることができます。
  * `max_results`: 返す結果の最大数（デフォルト = 100）。

# 戻り値

`:Name`、`:AcquisitionDate`、`:PublicationDate`、`:CloudCover`、および`:Id`の列を持つ`DataFrame`。

# 例

```julia
julia> geom = GeoDataFrames.read("test/data/roi.geojson").geometry[1];

julia> dates = (DateTime(2020, 8, 4), DateTime(2020, 8, 5));

julia> search("SENTINEL-2",  geom=geom, dates=dates)
3×5 DataFrame
 Row │ Name                               AcquisitionDate           Pub ⋯
     │ String                             String                    Str ⋯
─────┼───────────────────────────────────────────────────────────────────
   1 │ S2B_MSIL2A_20200804T183919_N0500…  2020-08-04T18:39:19.024Z  202 ⋯
   2 │ S2B_MSIL1C_20200804T183919_N0209…  2020-08-04T18:39:19.024Z  202
   3 │ S2B_MSIL1C_20200804T183919_N0500…  2020-08-04T18:39:19.024Z  202
                                                        3 columns omitted
```
