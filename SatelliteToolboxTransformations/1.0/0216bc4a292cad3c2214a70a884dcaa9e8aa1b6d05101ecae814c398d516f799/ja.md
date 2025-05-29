```
geodetic_to_ecef(geodetic_state::AbstractVector; ellipsoid::Ellipsoid{T} = wgs84_ellipsoid) where T<:Number -> SVector{3, T}
```

緯度 `lat` [rad]、経度 `lon` [rad]、および基準楕円体上の高度 `h` [m]（デフォルトはWGS-84）を地球中心・地球固定（ECEF）参照フレームで表されたベクトルに変換します。

!!! info
    アルゴリズムは**[1]**に基づいています。


# 参考文献

  * **[1]**: mu-blox ag (1999). Datum Transformations of GPS Positions. Application Note.
