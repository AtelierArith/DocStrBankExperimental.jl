```
do_deriv(dispatchlists, deltat::Float64=0.0)
do_deriv(dispatchlists, pa::ParameterAggregator, deltat::Float64=0.0)
```

1回の呼び出しで全体の導関数を計算するラッパー関数（初期化と実行メソッド）。`dispatchlists`は[`create_dispatch_methodlists`](@ref)からのものです。
