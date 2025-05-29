```
extract(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion
) -> nothing
```

GeoRegion `geo` の親 GeoRegion `geo.pID` から NASAPrecipitation データを抽出します。

!!! note
    `geo.pID` で特定される親 GeoRegion のデータは既に存在している必要があります。


# 引数

  * `npd` : データセットの詳細と日付ダウンロード範囲を指定する `NASAPrecipitationDataset`
  * `geo` : データ配列の経度-緯度の地理的範囲を設定する `GeoRegion` (詳細は [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl) を参照)
