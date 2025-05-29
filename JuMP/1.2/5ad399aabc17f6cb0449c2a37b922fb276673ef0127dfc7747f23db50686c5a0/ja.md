```
set_time_limit_sec(model::Model, limit::Float64)
```

ソルバーの時間制限（秒単位）を設定します。

[`unset_time_limit_sec`](@ref)を使用するか、`limit`を`nothing`に設定することで解除できます。

関連情報: [`unset_time_limit_sec`](@ref), [`time_limit_sec`](@ref).
