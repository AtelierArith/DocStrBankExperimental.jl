```
extract(
    npd  :: NASAPrecipitationDataset,
    sgeo :: GeoRegion,
    pgeo :: GeoRegion,
) -> nothing
```

GeoRegion `sgeo` のために、より大きな GeoRegion `pgeo` から NASAPrecipitation データを抽出します。

!!! note
    `pgeo` によって特定された親 GeoRegion のデータはすでに存在している必要があり、`sgeo` は `pgeo` の範囲内に完全に収まっている必要があります。


# 引数

  * `npd` : データセットの詳細と日付ダウンロード範囲を指定する `NASAPrecipitationDataset`
  * `sgeo` : データ配列の経度-緯度の地理的範囲を設定する `GeoRegion` (詳細は [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl) を参照)
  * `pgeo` : `sgeo` の「親」である `GeoRegion` であり、`sgeo` は `pgeo` の範囲内に完全に収まっている必要があります。
