```
along_track_distance(pos₁::Point, pos₂::Point, pos₃::Point[,radius::Float64=Rₑ_m])
```

`along_track_distance`は、開始点`pos₁` [deg]から、点`pos₃` [deg]に対する大円経路（点`pos₁`と`pos₂` [deg]で定義される）上の最も近い点までの距離を計算します。オプションで、地球の異なる`radius`を使用することができます。

出典: www.movable-type.co.uk/scripts/latlong.html
