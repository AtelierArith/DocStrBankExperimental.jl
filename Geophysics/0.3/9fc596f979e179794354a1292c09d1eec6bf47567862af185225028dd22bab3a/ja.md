```
pressure(h::Real=0,W::Weather=Standard) = pressure(W(h))
```

高度 `h` の `Weather` 列における単位面積あたりの絶対力 `P` (Pa または slug⋅ft⁻¹⋅s⁻²)。
