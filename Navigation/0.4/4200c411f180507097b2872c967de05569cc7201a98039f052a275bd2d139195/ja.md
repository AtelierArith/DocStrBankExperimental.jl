```
cross_track_distance(∠distance₁₃::Float64, bearing₁₂::Float64,
bearing₁₃::Float64[, radius::Float64=Rₑ_m])
```

点 `pos₃` [deg] から大円経路までの `cross_track_distance` [m] を返します。距離は、点 `pos₁` と `pos₃` [deg] の間の角距離、点 `pos₁` と `pos₃` [deg] の間の `bearing` [deg]、点 `pos₁` と `pos₂` [deg] の間の `bearing` [deg]、および地球の `radius` [m] を使用して計算されます。

出典: www.movable-type.co.uk/scripts/latlong.html
