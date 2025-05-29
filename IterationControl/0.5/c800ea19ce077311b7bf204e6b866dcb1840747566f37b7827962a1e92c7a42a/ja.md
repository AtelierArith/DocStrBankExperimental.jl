```
WithTrainingLossesDo(f=v->@info("training: $v"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、すなわち、`WithTrainingLossesDo(v->put!(my_losses, last(v))`。

`f(training_losses)`を呼び出します。ここで、`training_losses`は最新のバッチのトレーニング損失のベクトルです。

`stop_if_true`が`true`の場合、`f`が`true`を返した場合に早期停止をトリガーし、指定されている場合は`stop_message`をログに記録します。
