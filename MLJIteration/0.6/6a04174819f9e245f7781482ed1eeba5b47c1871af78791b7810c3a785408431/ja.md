```
WithReportDo(f=x->@info("report: $x"), stop_if_true=false, stop_message=nothing)
```

イテレーション制御、例えば、`WithReportDo(x->put!(my_channel, x))` のように。

`f(x)` を呼び出します。ここで `x = report(mach)` は、現在の状態におけるトレーニングマシン `mach` に関連付けられたレポートです。`stop_if_true` が `true` の場合、`f` が返す値が `true` の場合に早期停止をトリガーし、指定されている場合は `stop_message` をログに記録します。
