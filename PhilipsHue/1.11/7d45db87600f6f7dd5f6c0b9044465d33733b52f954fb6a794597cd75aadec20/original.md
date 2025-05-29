```
setlight(bridge::PhilipsHueBridge, light::Int, col::ColorTypes.Colorant)
setlight(B, 1, Colors.RGB(0.75, 0.25, 0.75))
setlight(B, 1, colorant"Pink")
```

Set color of a light using Colors.jl style colors. (You might need `using Colors`.)
