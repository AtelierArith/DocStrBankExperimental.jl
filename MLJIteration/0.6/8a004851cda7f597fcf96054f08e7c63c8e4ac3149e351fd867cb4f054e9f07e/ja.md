```
WithIterationsDo(f=x->@info("iterations: $x"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、例えば、`WithIterationsDo(x->put!(my_channel, x))` のように。

`f(x)` を呼び出します。ここで `x` は現在のモデルのイテレーション数（一般的には制御サイクルの数よりも多い）です。`stop_if_true` が `true` の場合、`f` が `true` を返すと早期停止をトリガーし、指定されている場合は `stop_message` をログに記録します。
