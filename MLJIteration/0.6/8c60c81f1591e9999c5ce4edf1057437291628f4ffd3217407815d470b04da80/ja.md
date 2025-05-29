```
WithFittedParamsDo(f=x->@info("fitted_params: $x"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、例えば、`WithFittedParamsDo(x->put!(my_channel, x))` のように。

`f(x)` を呼び出します。ここで `x = fitted_params(mach)` は、現在の状態におけるトレーニングマシン `mach` のフィッティングパラメータです。`stop_if_true` が `true` の場合、`f` が返す値が `true` のときに早期停止をトリガーし、指定されている場合は `stop_message` をログに記録します。
