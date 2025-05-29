```
read(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion,
    dt  :: TimeType;
    lonlat :: Bool = false
) -> NCDataset           (if lonlat = false)
  -> lon, lat, NCDataset (if lonlat = true)
```

指定された `npd` の NASA 降水量データセットを、指定された `geo` の GeoRegion で、指定された `dt` の日付で読み込みます。

# 引数

  * `e5ds` : データセットの詳細と日付ダウンロード範囲を指定する `NASAPrecipitationDataset`
  * `ereg` : データ配列の経度-緯度の地理的範囲を設定する `GeoRegion` (詳細は [GeoRegions.jl](https://github.com/JuliaClimate/GeoRegions.jl) を参照)
  * `dt`   : 指定された日付。取得される NCDataset にはその日付のデータが含まれる場合がありますが、`npd` で指定された `NASAPrecipitationDataset` によっては他の日付のデータも含まれる可能性があります。

# キーワード引数

  * `lonlat` : `true` の場合、データセットの経度と緯度のベクトルを返します。そうでない場合は NCDataset 型のみが返されます。
