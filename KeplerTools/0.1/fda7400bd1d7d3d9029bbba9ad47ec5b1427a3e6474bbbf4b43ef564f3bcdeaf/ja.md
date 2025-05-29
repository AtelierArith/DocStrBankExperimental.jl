```
orb = fast_arrival_orbit(pkorb, v̄rel, tₛₚ)
```

駐機軌道 `pkorb`、パッチでの相対速度 `v̄rel`、パッチでの時間 `tₛₚ` から到着軌道を計算します。

この関数は `arrival_orbit` よりも高速ですが、非常に楕円形の駐機軌道に対しては最適でない軌道を返す可能性があります。
