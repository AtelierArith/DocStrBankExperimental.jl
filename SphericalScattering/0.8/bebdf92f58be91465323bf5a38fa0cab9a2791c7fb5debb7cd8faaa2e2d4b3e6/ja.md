```
ex = HertzianDipole(
        embedding   = Medium(ε0, μ0),
        frequency   = error("missing argument `frequency`"),
        amplitude   = 1.0,
        position    = error("missing argument `position`"),
        orientation = SVector{3,typeof(frequency)}(0.0, 0.0, 1.0),
)
```
