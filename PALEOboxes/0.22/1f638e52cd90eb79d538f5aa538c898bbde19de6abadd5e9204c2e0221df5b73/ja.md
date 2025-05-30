```
do_deriv(dispatchlists, deltat::Float64=0.0)
do_deriv(dispatchlists, pa::ParameterAggregator, deltat::Float64=0.0)
```

ラッパー関数は、1回の呼び出しで全体の導関数（初期化と実行メソッド）を計算します。 `dispatchlists` は [`create_dispatch_methodlists`](@ref) からのものです。
