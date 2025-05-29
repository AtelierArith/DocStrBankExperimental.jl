```julia
log_with_time_derivative(t, twist)

```

指数座標とその時間微分を一度に計算します。これは主に、ForwardDiffが`log`の特異点で機能しないために存在します。この場合、ForwardDiffよりも約50%速いです。
