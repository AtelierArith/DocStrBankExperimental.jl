```
geodetic_to_geocentric(ϕ_gd::Number, h::Number; ellipsoid::Ellipsoid{T} = WGS84_ELLIPSOID) where T<:Number -> T, T
```

地理緯度 `ϕ_gd` (-π/2, π/2) [rad] と基準楕円体上の高さ `h` [m] から地心緯度と半径を計算します（デフォルトは WGS-84）。経度は地心座標と地理座標の両方で同じであることに注意してください。

!!! info
    アルゴリズムは **[1]**(p. 3) に基づいています。


# 戻り値

  * `T`: 地心緯度 [rad].
  * `T`: 地球の中心からの半径 [m].

# 参考文献

  * **[1]** ISO TC 20/SC 14 N (2011). ジオ磁気基準モデル.
