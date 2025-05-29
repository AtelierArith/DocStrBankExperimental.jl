```
orb = fast_departure_orbit(pkorb, v̄rel, tₛₚ)
```

駐機軌道 `pkorb` からの出発軌道、パッチでの相対速度 `v̄rel`、パッチでの時間 `tₛₚ` を計算します。

この関数は `departure_orbit` よりも高速ですが、非常に楕円形の駐機軌道に対しては最適でない軌道を返す可能性があります。
