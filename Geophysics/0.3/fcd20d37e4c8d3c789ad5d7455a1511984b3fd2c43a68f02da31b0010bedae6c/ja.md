```
elasticity(h::Real=0,W::Weather=Standard) = elasticity(W(h))
```

気象地点の高度 `h` における弾性率 `B` (Pa または slug⋅ft⁻¹⋅s⁻²)。
