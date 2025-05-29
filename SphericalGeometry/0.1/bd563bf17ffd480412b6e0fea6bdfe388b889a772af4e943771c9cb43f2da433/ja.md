```
angular_distance(point₃::Point, point₁::Point, azimuth₁₂::Float64)
```

点₃ [deg] から点₁ [deg] で始まる大円の最も近い点までの `angular_distance` [deg] を返します。`azimuth₁₂` [deg] は点₁から点₂へのものです。大円は点₂で止まらず、単位球の周りを連続していると仮定されます。正の値は線の右側に、負の値は線の左側にいることを示します。

出典: www.movable-type.co.uk/scripts/latlong.html
