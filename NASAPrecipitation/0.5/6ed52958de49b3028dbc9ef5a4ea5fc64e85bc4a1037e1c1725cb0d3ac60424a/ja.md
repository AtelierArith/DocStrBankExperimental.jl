```
npdfnc(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion,
    dt  :: TimeType
) -> String
```

指定された `npd` の NASA 降水量データセットのファイルパスを、指定された `geo` の GeoRegion と、指定された `dt` の日付で返します。

# 引数

  * `npd` : データセットの詳細と日付ダウンロード範囲を指定する `NASAPrecipitationDataset`
  * `geo` : データ配列の経度-緯度の地理的範囲を設定する `GeoRegion` (詳細は [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl) を参照)
  * `dt`  : 指定された日付。取得される NCDataset にはその日付のデータが含まれる場合がありますが、`npd` で指定された `NASAPrecipitationDataset` によっては他の日付のデータも含まれる可能性があります。
