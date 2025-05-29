```
getLandSea(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion = GeoRegion("GLB");
    returnlsd = true,
    FT = Float32
) -> LandSea
```

指定された `NASAPrecipitationDataset` の陸海マスクデータを取得します。

# 引数

  * `npd` : 指定された `NASAPrecipitationDataset` で、IMERG または TRMM のいずれかであり、関数は追加の指定なしに関連する陸海マスクをダウンロードします。
  * `geo` : 興味のある GeoRegion

# キーワード引数

  * `returnlsd` : `true` の場合、データを `LandSea` データセットとして返します。そうでない場合、データは単に npd.maskpath ディレクトリに保存されます。
