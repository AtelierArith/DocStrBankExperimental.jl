```
isinERA5Region(
    point :: Point2{<:Real},
    e5geo :: ERA5Region;
    tlon  :: Real = 0,
    tlat  :: Real = 0,
    throw :: Bool = true
) -> Bool
```

地理的な点 `Point` が `e5geo` で定義された ERA5Region 内にあるかどうかを確認します。

# 引数

  * `point` : `Point2` 型の地理的な点。`Point2(plon,plat)` を渡します。ここで、`plon` は点の経度、`plat` は緯度です。
  * `e5geo` : ERA5Region 構造体コンテナ

# キーワード引数

  * `tlon`  : 経度の境界の閾値
  * `tlat`  : 緯度の境界の閾値
  * `throw` : `true` の場合、`Point` が `geo` 内にないときにエラーが発生し、プログラムの実行が停止します。
