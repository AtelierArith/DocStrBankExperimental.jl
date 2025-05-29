```
angular_distance(angular_distance₁₃::Float64, azimuth₁₃::Float64,
azimuth₁₂::Float64)
```

点₃ [deg] から `point₁` [deg] で始まる大円上の最も近い点までの `angular_distance` [deg] を返します。計算には、`point₁` と `point₃` [deg] の間の `angular_distance₁₃` と `azimuth₁₃`、および大円上の `point₁` から `point₂` への `azimuth₁₂` が必要です。大円は `point₂` で止まることはなく、単位球の周りを連続していると仮定します。

出典: www.movable-type.co.uk/scripts/latlong.html
