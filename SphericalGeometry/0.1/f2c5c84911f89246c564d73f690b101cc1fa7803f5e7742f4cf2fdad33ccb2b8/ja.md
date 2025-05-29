```
intersection_point(point₁::Point, point₂::Point, azimuth₁₃::Float64,
azimuth₂₃::Float64)
```

2つの始点 [deg] `point₁` と `point₂` [deg] からの2つの大円の交点 `point₃` [deg] を返します。`point₁` から `point₃` [deg] への方位角と `point₂` から `point₃` [deg] への方位角の2つの方位角 [deg] が与えられます。

特定の状況下では、結果が ∞ または *あいまいな解* になることがあります。

出典: edwilliams.org/avform.htm
