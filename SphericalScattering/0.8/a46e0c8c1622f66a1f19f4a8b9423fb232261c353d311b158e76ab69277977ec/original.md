```
ex = electricRingCurrent(;
        embedding   = Medium(ε0, μ0),
        frequency   = error("missing argument `frequency`"),
        amplitude   = 1.0,
        radius      = error("missing argument `radius`"),
        center      = error("missing argument `center`"),
        orientation = SVector{3,typeof(frequency)}(0.0, 0.0, 1.0),
)
```
