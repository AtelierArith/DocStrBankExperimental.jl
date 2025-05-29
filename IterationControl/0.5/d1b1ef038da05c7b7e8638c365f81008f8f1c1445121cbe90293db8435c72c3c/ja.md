```
Callback(f=_->nothing, stop_if_true=false, stop_message=nothing, raw=false)
```

イテレーション制御、すなわち、`Callback(m->put!(v, my_loss_function(m))`。

`f(IterationControl.expose(m))`を呼び出します。ここで、`m`はイテレートされているオブジェクトです。ただし、`raw=true`の場合は`f(m)`を呼び出します（`expose`がオーバーロードされていない場合は保証されます）。`stop_if_true`が`true`の場合、`f`が返す値が`true`であれば早期停止をトリガーし、指定されている場合は`stop_message`をログに記録します。
