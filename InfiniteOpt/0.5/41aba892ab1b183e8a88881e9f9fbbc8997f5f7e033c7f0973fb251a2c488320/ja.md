```
JuMP.unset_time_limit_sec(model::InfiniteModel)
```

`unset_time_limit_sec`を拡張して、ソルバーの時間制限を解除します。`set_time_limit_sec`を使用して設定できます。

**例**

```julia-repl
julia> unset_time_limit_sec(model)
```
