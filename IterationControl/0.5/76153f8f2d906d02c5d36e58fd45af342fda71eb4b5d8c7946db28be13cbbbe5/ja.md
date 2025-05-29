```
WithLossDo(f=x->@info("loss: $x"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、例えば、`WithLossDo(x->put!(my_losses, x))` のように。

`f(loss)` を呼び出します。ここで `loss` は現在の損失です。

`stop_if_true` が `true` の場合、`f` が返す値が `true` の場合に早期停止をトリガーし、指定されている場合は `stop_message` をログに記録します。
