```
simulate_scenarios(
    model::StateSpaceModel, steps_ahead::Int, n_scenarios::Int;
    filter::KalmanFilter=default_filter(model)
) -> Array{<:AbstractFloat, 3}
```

`steps_ahead`のために、望ましい`filter`を使用して`n_scenarios`の未来のシナリオをモンテカルロシミュレーションでサンプリングします。
