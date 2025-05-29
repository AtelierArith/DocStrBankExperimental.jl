```
smoothing(;
    npd :: Union{IMERGHalfHourly},
    geo :: GeoRegion = GeoRegion("GLB");
    spatial  :: Bool = false,
    temporal :: Bool = false,
    hours     :: Real = 0,
    smoothlon :: Real = 0,
    smoothlat :: Real = 0,
    verbose :: Bool = false
)
```

NASAPrecipitationデータセットの指定された日付にわたる空間時間スムージングを実行します `npd` NASAPrecipitationDataset と `geo` GeoRegion。

# キーワード引数

  * `spatial` : `true` の場合、空間スムージングを実行します
  * `temporal` : `true` の場合、時間スムージングを実行します
  * `hours` : 時間スムージングが実行される時間数。タイムステップの整数倍でなければなりません。
  * `smoothlon` : スムージングを行う経度の度数。`npd` データセットの解像度の整数倍でなければなりません。
  * `smoothlat` : スムージングを行う緯度の度数。`npd` データセットの解像度の整数倍でなければなりません。
  * `verbose` : `true` の場合、追加のログを行います
