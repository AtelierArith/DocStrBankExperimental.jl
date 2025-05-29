```
RegionGrid(
    geo :: TiltRegion,
    lon :: Union{Vector{<:Real},AbstractRange{<:Real},
    lat :: Union{Vector{<:Real},AbstractRange{<:Real}
) -> ggrd :: RLinearMask
```

指定された引数に基づいて `RectGrid` または `PolyGrid` タイプを作成します。このメソッドは、Iscaや衛星および再解析グリッドデータセットからの経度/緯度出力のための直交グリッドに適しています。

# 引数

  * `geo` : 興味のあるGeoRegion
  * `lon` : 経度ポイントを含むベクターまたは `AbstractRange`
  * `lat` : 緯度ポイントを含むベクターまたは `AbstractRange`

# 戻り値

  * `ggrd` : `RectilinearGrid`
