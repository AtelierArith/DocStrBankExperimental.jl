```
smoothing(;
    npd :: Union{IMERGDaily,TRMMDaily},
    geo :: GeoRegion;
    spatial  :: Bool = false,
    temporal :: Bool = false,
    days :: Int = 0,
    smoothlon :: Real = 0,
    smoothlat :: Real = 0,
    verbose :: Bool = false
)
```

指定された`npd` NASAPrecipitationDatasetおよび`geo` GeoRegionの日付にわたって、日次NASAPrecipitationデータセットの空間時間スムージングを実行します。

# キーワード引数

  * `spatial` : `true`の場合、空間スムージングを実行します
  * `temporal` : `true`の場合、時間的スムージングを実行します
  * `days` : 時間的スムージングが実行される日数。整数でなければなりません。
  * `smoothlon` : スムージングを行う経度の度数。`npd`データセットの解像度の整数倍でなければなりません。
  * `smoothlat` : スムージングを行う緯度の度数。`npd`データセットの解像度の整数倍でなければなりません。
  * `verbose` : `true`の場合、追加のログを行います
