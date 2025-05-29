```
WithModelDo(f=x->@info("model: $x"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、例えば、`WithModelDo(x->put!(my_channel, x))` のように。

`f(x)` を呼び出します。ここで `x` はトレーニングマシンに関連付けられたモデルです。`f` は `x` を変更することができます。例えば、`f(x) = (x.learning_rate *= 0.9)` のように。`stop_if_true` が `true` の場合、`f` が返す値が `true` のときに早期停止をトリガーし、指定されている場合は `stop_message` をログに記録します。
