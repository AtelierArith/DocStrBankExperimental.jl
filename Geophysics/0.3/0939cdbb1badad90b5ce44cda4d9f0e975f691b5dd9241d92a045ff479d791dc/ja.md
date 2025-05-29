```
sonicspeed(h::Real=0,W::Weather) = sonicspeed(temperature(h,W),fluid(W))
```

天候の地点 `W` における高度 `h` での音波の擾乱の速度 (m⋅s⁻¹ または ft⋅s⁻¹)。
