```
read(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion,
    dt  :: TimeType;
    smooth   :: Bool = false,
    smoothlon  :: Real = 0,
    smoothlat  :: Real = 0,
    smoothtime :: Real = 0,
    quiet  :: Bool = false
) -> NCDataset
```

指定された `npd` による NASA 降水量データセットを、指定された `geo` による GeoRegion で、指定された `dt` の日付で読み込みます。

# 引数

  * `npd` : データセットの詳細と日付ダウンロード範囲を指定する `NASAPrecipitationDataset`
  * `geo` : データ配列の経度-緯度の地理的範囲を設定する `GeoRegion` (詳細は [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl) を参照)
  * `dt`  : 指定された日付。取得される NCDataset にはその日付のデータが含まれる場合がありますが、`npd` によって指定された `NASAPrecipitationDataset` に応じて他の日付のデータも含まれる可能性があります。

# キーワード引数

  * `smooth` :
  * `smoothlon` :
  * `smoothlat` :
  * `smoothtime` :
  * `quiet` :
