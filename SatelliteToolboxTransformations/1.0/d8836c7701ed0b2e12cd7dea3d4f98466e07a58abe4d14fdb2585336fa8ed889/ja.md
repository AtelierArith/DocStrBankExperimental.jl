```
ecef_to_geodetic(r_e::AbstractVector; ellipsoid::Ellipsoid{T} = WGS84_ELLIPSOID) where T<:Number -> NTuple{3, T}
```

地球中心、地球固定 (ECEF) 参照フレームで表されたベクトル `r_e` [m] を、カスタムターゲット楕円体の測地座標に変換します（デフォルトは WGS-84）。

!!! info
    アルゴリズムは **[1]** に基づいています。


# 戻り値

  * `T`: 緯度 [rad].
  * `T`: 経度 [rad].
  * `T`: 高度 [m].

# 参考文献

  * **[1]**: mu-blox ag (1999). Datum Transformations of GPS Positions. Application Note.
