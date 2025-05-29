```
area(c::ConnectingOrbit; origin::AbstractArray=[0.0,0.0],
     i_p::Integer=1, rtol=1e-8)
```

Get the "area" of a connecting orbit ∫₋₁¹ (x dy/ds - y dy/ds) ds
