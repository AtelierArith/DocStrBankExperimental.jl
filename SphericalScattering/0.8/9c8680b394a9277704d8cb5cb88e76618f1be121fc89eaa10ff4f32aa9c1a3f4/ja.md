```
ex = planeWave(;
        embedding    = Medium(ε0, μ0),
        frequency    = error("missing argument `frequency`"),
        amplitude    = 1.0,
        direction    = SVector{3,typeof(frequency)}(0.0, 0.0, 1.0),
        polarization = SVector{3,typeof(frequency)}(1.0, 0.0, 0.0),
)
```
