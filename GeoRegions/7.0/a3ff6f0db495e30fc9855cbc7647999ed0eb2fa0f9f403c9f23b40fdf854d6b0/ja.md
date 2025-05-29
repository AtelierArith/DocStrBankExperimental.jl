```
coordinates(
    geo :: GeoRegion;
    n :: Int = 1
) -> lon :: Vector{<:Real}, lat :: Vector{<:Real}
```

与えられたGeoRegionに対して、形状の経度と緯度のベクトルを作成します。

# 引数

  * `geo` : GeoRegion。
  * `n` : 形状の各辺のセグメント数。

# 戻り値

  * `lon` : GeoRegionの形状の経度ポイントのベクトル。
  * `lat` : GeoRegionの形状の緯度ポイントのベクトル。
