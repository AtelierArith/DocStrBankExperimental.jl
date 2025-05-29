```
make_weighted_healpix_geom_info(
    nside::Integer, stride::Integer, weight::AbstractArray{T}
    ) where T <: Real
```

HEALPixに対応するジオメトリ構造体を初期化します。

# 引数

  * `nside::Integer`: HEALPixの解像度パラメータ
  * `stride::Integer`: リング内の連続するピクセル間のストライド
  * `weight::AbstractArray{T}`: マップ分析中にすべてのピクセルに掛け算される重み（通常はリング内のピクセルの固体角）

# 戻り値

  * `GeomInfo`オブジェクト
