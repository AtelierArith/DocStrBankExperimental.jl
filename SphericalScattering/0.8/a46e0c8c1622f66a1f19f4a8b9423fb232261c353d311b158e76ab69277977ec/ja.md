```
ex = electricRingCurrent(;
        embedding   = Medium(ε0, μ0),
        frequency   = error("引数 `frequency` が不足しています"),
        amplitude   = 1.0,
        radius      = error("引数 `radius` が不足しています"),
        center      = error("引数 `center` が不足しています"),
        orientation = SVector{3,typeof(frequency)}(0.0, 0.0, 1.0),
)
```
