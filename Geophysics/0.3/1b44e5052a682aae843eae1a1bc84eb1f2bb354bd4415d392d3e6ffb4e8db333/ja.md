```
prandtl(h::Real=0,W::Weather) = prandtl(temperature(h,W),fluid(W))
```

気象地点の高度 `h` におけるプラントル数（無次元）。
