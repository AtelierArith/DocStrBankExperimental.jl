```
search(cat::Catalog, collections, lon_range, lat_range, datetime;
       limit = 200,
       filter = nothing,
       query = nothing,
)
```

`STAC.Catalog` `cat` に属するアイテムを、`collections` 内で経度範囲 `lon_range`（開始および終了経度）、緯度範囲 `lat_range`、および時間範囲（開始および終了 `DateTime`）で検索します。

オプションの `filter` パラメータを使用すると、[CQL2](https://github.com/stac-api-extensions/filter) を使用して結果をフィルタリングできます（以下の例を参照）。オプションの `query` パラメータを介して [STACQL](https://github.com/stac-api-extensions/query/blob/3c42ab316dbba0089803e77fb572dc0cfc4ee4fe/README.md) もサポートされています。CQL2 を STACQL の代わりに使用することをお勧めします。この `filter` と `query` は実験的であり、現在 STAC の「候補」または「パイロット」の一部です。

関数 `search` は、検索結果を持つ julia `Channel` を返し、これは一度だけ反復処理できます。結果を保存する必要がある場合は、`search_results = collect(search(cat,...))` を使用します。

例:

```julia
using STAC, Dates
collections = ["landsat-8-c2-l2"]
time_range = (DateTime(2018,01,01), DateTime(2018,01,02))
lon_range = (2.51357303225, 6.15665815596)
lat_range = (49.5294835476, 51.4750237087)

catalog = STAC.Catalog("https://planetarycomputer.microsoft.com/api/stac/v1")

search_results = collect(search(catalog, collections, lon_range, lat_range, time_range))
```

追加の CQL2 フィルタを使用した例

```julia
filter = Dict(
   "op" => "<=",
   "args" => [Dict("property" => "eo:cloud_cover"), 61]
)

search_results = collect(
        search(cat, collections,
               lon_range, lat_range, time_range,
               filter = filter,
))
```

現在、POST 検索リクエストのみがサポートされています。
