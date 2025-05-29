```
RegionGrid(
    e5geo :: ERA5Region{ST,FT},
    lon   :: Array{<:Real},
    lat   :: Array{<:Real}
) -> GeoRegion.RegionGrid
```

ERA5Regionから生データを抽出するために必要な情報とマスク情報を含むRegionGridを作成します。

# 引数

  * `e5geo` : ERA5Region構造体タイプ
  * `lon`   : 経度ポイントを含む配列
  * `lat`   : 緯度ポイントを含む配列
