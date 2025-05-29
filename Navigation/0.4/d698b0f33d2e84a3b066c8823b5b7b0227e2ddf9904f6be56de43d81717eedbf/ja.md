```
intersection_point(pos₁::Point, pos₂::Point, bearing₁₃::Float64, bearing₂₃::Float64)
```

2つの始点 [deg] `pos₁` と `pos₂` [deg] および `pos₁` から `pos₃` [deg] への2つの方位 [deg] と `pos₂` から `pos₃` [deg] への方位 [deg] が与えられたとき、2つの大円経路の交点 `pos₃` を返します。

特定の状況下では、結果が ∞ または *あいまいな解* になることがあります。

出典: edwilliams.org/avform.htm
