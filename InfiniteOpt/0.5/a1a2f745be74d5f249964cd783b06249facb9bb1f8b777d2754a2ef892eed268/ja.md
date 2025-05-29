```
JuMP.set_time_limit_sec(model::InfiniteModel, limit)
```

`set_time_limit_sec`を拡張して、ソルバーの時間制限（秒単位）を設定します。`unset_time_limit_sec`を使用するか、`limit`を`nothing`に設定することで解除できます。

**例**

```julia-repl
julia> set_time_limit_sec(model, 100)
100
```
