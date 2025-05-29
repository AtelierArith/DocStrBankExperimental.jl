```
geocentric_to_ecef(geocentric_state::AbstractVector) -> SVector{3, T}
```

地心座標（緯度 `lat` [rad]、経度 `lon` [rad]、および地球中心からの距離 `r` [m]）を地球中心・地球固定ベクトル [m] に変換します。
