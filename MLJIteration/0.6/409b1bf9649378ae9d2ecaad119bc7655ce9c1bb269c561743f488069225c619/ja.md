```
WithEvaluationDo(f=x->@info("評価: $x"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、例えば、`WithEvaluationDo(x->put!(my_channel, x))` のように。

`f(x)` を呼び出します。ここで `x` は、`evaluate!(train_mach, resampling=..., ...)` によって返される最新のパフォーマンス評価です。`resampling=nothing` の場合は無効です。`stop_if_true` が `true` の場合、`f` によって返される値が `true` の場合は早期停止をトリガーし、指定されている場合は `stop_message` をログに記録します。
