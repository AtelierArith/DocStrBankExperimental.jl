```
focus_chart( ; radius=1, nspoke=30, value=1)
```

Generate `nspoke` Triangle phantom parameters for a focus chart. Returns `Vector{Object2d{Triangle}` for passing to `phantom`.

# Options

  * `radius::RealU = 1` radius of phantom
  * `nspoke::Int = 60` # of spokes
  * `value::Number = 1` alternate between 0 and this value
