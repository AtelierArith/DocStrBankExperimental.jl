```
along_track_distance(∠distance₁₃::Float64, cross_track_∠distance::Float64,
[radius::Float64=Rₑ_m])
```

`along_track_distance` は、開始点 `pos₁` [deg] から大円経路上の最も近い点までの距離を計算します（`pos₁` と `pos₃` [deg] の間の角距離 `∠distance₁₃` [deg] と、点 `pos₃` [deg] までの横断角距離 `cross_track_∠distance` [deg] によって定義されます）。オプションで、地球の異なる `radius` を使用することができます。

出典: www.movable-type.co.uk/scripts/latlong.html
