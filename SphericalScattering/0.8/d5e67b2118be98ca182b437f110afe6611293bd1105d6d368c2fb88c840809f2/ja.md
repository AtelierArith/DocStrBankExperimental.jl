```
ex = SphericalModeTE(;
        embedding   = Medium(ε0, μ0),
        frequency   = error("missing argument `frequency`"),
        amplitude   = 1.0,
        m           = 0,
        n           = 1,
        c           = 1,
        center      = SVector{3,typeof(frequency)}(0.0, 0.0, 0.0),
        orientation = SVector{3,typeof(frequency)}(0.0, 0.0, 1.0),
)
```
