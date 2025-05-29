```
area(c::ConnectingOrbit; origin::AbstractArray=[0.0,0.0],
     i_p::Integer=1, rtol=1e-8)
```

接続軌道の「面積」を取得します ∫₋₁¹ (x dy/ds - y dy/ds) ds
