```
WithNumberDo(f=n->@info("number: $n"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、例えば、`WithNumberDo(n->put!(my_channel, n))` のように。

`f(n + 1)` を呼び出します。ここで `n` は制御サイクルの完了数です（したがって、`n = 1, 2, 3, ...`、制御が [`IterationControl.skip`](@ref) にラップされていない限り）。

`stop_if_true` が `true` の場合、`f` が `true` を返した場合に早期停止をトリガーし、指定されている場合は `stop_message` をログに記録します。
