```
smoothing(;
    npd :: Union{IMERGMonthly,TRMMMonthly},
    geo :: GeoRegion;
    smoothlon :: Real = 0,
    smoothlat :: Real = 0,
    verbose :: Bool = false
)
```

指定された日付の**月次**NASAPrecipitationデータセットに対して、`npd` NASAPrecipitationDatasetおよび`geo` GeoRegionにわたる空間スムージングを実行します。

!!! warning
    IMERGMonthlyおよびTRMMMonthlyデータセットに対しては、時間的スムージング***は***実行できません。これらは空間的にのみスムージングできます。


# キーワード引数

  * `smoothlon` : スムージングする経度の度数。`npd`データセットの解像度の整数倍でなければなりません。
  * `smoothlat` : スムージングする緯度の度数。`npd`データセットの解像度の整数倍でなければなりません。
  * `verbose` : `true`の場合、追加のログを行います。
