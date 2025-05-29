```
evaluate(x, δt)
```

`x::AbstractArray{Taylor1{T}}`の各要素を、ODEの従属変数として、*時間* δt で評価します。`x(δt)`という構文は`evaluate(x, δt)`と同等であり、`x()`は`evaluate(x)`と同等です。
