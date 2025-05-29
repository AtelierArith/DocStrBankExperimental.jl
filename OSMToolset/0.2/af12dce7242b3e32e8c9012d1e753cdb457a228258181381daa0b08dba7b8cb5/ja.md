```
find_poi(filename::AbstractString, scrape_config::ScrapePOIConfig{T <: AbstractMetaPOI}=ScrapePOIConfig(); all_tags::Bool=false)
```

指定されたXML `filename` から興味のあるポイントを持つ `DataFrame` を生成します。`scrape_config` パラメータはスクレイピングプロセスの設定を定義します。データフレームには各POIのタイプ `T` のメタデータも含まれます。

`DataFrame` は後で `AttractivenessSpatIndex` と共に使用して、魅力的な空間インデックスを構築することができます。

`all_tags` パラメータを `true` に設定すると、タグが一致した場合、同じ要素内の隣接するタグも結果のデータフレームに含まれるようになります。
