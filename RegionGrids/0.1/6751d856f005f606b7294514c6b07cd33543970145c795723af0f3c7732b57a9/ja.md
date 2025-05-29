```
RegionGrid(
    geo :: GeoRegion,
    lon :: Union{Vector{<:Real},AbstractRange{<:Real},
    lat :: Union{Vector{<:Real},AbstractRange{<:Real};
    rotation  :: Real = 0,
    sigdigits :: Int = 10
) -> ggrd :: RectilinearGrid
```

指定された引数に基づいて `RectilinearGrid` 型を作成します。このメソッドは、Isca からの出力や衛星および再解析グリッドデータセットからの経度/緯度の出力に適した直交グリッドに適しています。

# 引数

  * `geo` : 興味のある GeoRegion。
  * `lon` : 経度ポイントを含むベクターまたは `AbstractRange`。
  * `lat` : 緯度ポイントを含むベクターまたは `AbstractRange`。

# キーワード引数

  * `rotation` : GeoRegion セントロイドの周りで最終的な「デローテーション」データを X-Y デカルト座標系（メートル単位）に投影するための回転角度（度単位）。`geo.θ` に対して正の値は、セントロイドの周りで最終値を反時計回りに回転させます。デフォルトは 0 です。

# 戻り値

  * `ggrd` : `RectilinearGrid`。
