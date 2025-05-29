```
function slider(vals::AbstractArray;
                value=medianelement(vals),
                label=nothing, readout=true, kwargs...)
```

`vals`の値を取るスライダーウィジェットを作成し、スライダーが変更されるとobservable `value`を更新します。
