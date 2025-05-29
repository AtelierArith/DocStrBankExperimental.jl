```
geocentric_to_geodetic(ϕ_gc::Number, r::Number; ellipsoid::Ellipsoid{T} = WGS84_ELLIPSOID) where T<:Number -> T, T
```

地心緯度 `ϕ_gc` (-π/2, π/2) [rad] と半径 `r` [m] から、基準楕円体（デフォルトはWGS-84）上の測地線緯度と高度を計算します。経度は地心座標と測地座標の両方で同じであることに注意してください。

!!! info
    アルゴリズムは **[1]** に基づいています。


# 戻り値

  * `T`: 測地線緯度 [rad].
  * `T`: 基準楕円体（デフォルトはWGS-84）上の高度 [m].

# 参考文献

  * **[1]** Borkowski, K. M (1987). Transformation of geocentric to geodetic coordinates   without approximations. Astrophysics and Space Science, vol.  139, pp. 1-4.

```
