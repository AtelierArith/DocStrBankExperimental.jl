```
RegionGrid(
    geo :: Union{RectRegion,PolyRegion},
    lon :: Union{Vector{<:Real},AbstractRange{<:Real},
    lat :: Union{Vector{<:Real},AbstractRange{<:Real}
) -> ggrd :: RLinearMask
```

指定された引数に基づいて `RectGrid` または `PolyGrid` タイプを作成します。このメソッドは、Isca からの出力や、衛星および再解析グリッドデータセットからの経度/緯度の出力に適しています。

# 引数

  * `geo` : 興味のある GeoRegion
  * `lon` : 経度ポイントを含むベクトルまたは `AbstractRange`
  * `lat` : 緯度ポイントを含むベクトルまたは `AbstractRange`

# 戻り値

  * `ggrd` : `RectilinearGrid`
