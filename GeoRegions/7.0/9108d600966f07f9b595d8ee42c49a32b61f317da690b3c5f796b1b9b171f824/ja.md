```
in(
    point :: Point2{<:Real},
    geo   :: GeoRegion;
    throw :: Bool = false
) -> tf :: Bool
```

地理的な点 `point` が `geo` で定義された GeoRegion 内にあるかどうかを確認します。

# 引数

  * `point` : `Point` 型の地理的な点。`Point(plon,plat)` を渡します。ここで、`plon` と `plat` は点の経度と緯度です。
  * `geo`   : GeoRegion 構造体コンテナ。

# キーワード引数

  * `throw` : `true` の場合、`point` が `geo` 内にないときにエラーが発生し、プログラムの実行が停止します。

# 戻り値

  * `tf` : `true`/`false` のブール値。
