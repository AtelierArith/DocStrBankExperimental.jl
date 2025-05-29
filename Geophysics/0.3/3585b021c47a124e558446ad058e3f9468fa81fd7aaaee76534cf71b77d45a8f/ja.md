```
heatratio(h::Real=0,W::Weather) = heatratio(temperature(h,W),fluid(W))
```

特定熱比 `γ` は、`Weather` の位置の高度 `h` での値（無次元）。
