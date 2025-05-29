```
JuMP.time_limit_sec(model::InfiniteModel)
```

`time_limit_sec`を拡張して、最適化モデルによって使用される解の時間制限（秒単位）を取得します（設定されていない場合は`nothing`）。`set_time_limit_sec`を使用して設定できます。

**例**

```julia-repl
julia> time_limit_sec(model)
100
```
