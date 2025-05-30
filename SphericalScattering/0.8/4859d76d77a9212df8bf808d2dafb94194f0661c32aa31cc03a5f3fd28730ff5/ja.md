```
ex = FitzgeraldDipole(;
        embedding   = Medium(ε0, μ0),
        frequency   = error("引数 `frequency` が不足しています"),
        amplitude   = 1.0,
        position    = error("引数 `position` が不足しています"),
        orientation = SVector{3,typeof(frequency)}(0.0, 0.0, 1.0),
)
```
