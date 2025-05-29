```
download(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion = GeoRegion("GLB");
    overwrite :: Bool = false
) -> nothing
```

指定された `npd` の NASA 降水量データセットを、指定された `geo` の GeoRegion に対してダウンロードします。

# 引数

  * `npd` : データセットの詳細と日付ダウンロード範囲を指定する `NASAPrecipitationDataset`
  * `geo` : データ配列の経度-緯度の地理的範囲を設定する `GeoRegion` (詳細は [GeoRegions.jl](https://github.com/GeoRegionsEcosystem/GeoRegions.jl) を参照)

# キーワード引数

  * `overwrite` : `true` の場合、既存のファイルを上書きします
