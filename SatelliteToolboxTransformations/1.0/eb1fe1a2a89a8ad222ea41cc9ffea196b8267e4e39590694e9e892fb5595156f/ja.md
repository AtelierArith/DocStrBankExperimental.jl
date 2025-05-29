```
geocentric_to_geodetic(geocentric_state::AbstractVector; ellipsoid::Ellipsoid{T} = WGS84_ELLIPSOID) where T<:Number -> T, T
```

地心緯度 `ϕ_gc` (-π/2, π/2) [rad] と半径 `r` [m] から、基準楕円体上の測地緯度と高度を計算します（デフォルトはWGS-84）。経度は地心座標と測地座標の両方で同じであることに注意してください。

!!! info
    経度は状態間で同じであるため、地心状態ベクトルには緯度と半径のみが含まれます。

    アルゴリズムは**[1]**に基づいています。


# 戻り値

  * `T`: 測地緯度 [rad].
  * `T`: 基準楕円体上の高度（デフォルトはWGS-84） [m].

# 参考文献

  * **[1]** Borkowski, K. M (1987). Transformation of geocentric to geodetic coordinates   without approximations. Astrophysics and Space Science, vol.  139, pp. 1-4.

```
