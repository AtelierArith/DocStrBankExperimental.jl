```
set_time_limit_sec(model::GenericModel, limit::Float64)
```

ソルバーの時間制限（秒単位）を設定します。

[`unset_time_limit_sec`](@ref)を使用するか、`limit`を`nothing`に設定することで解除できます。

関連情報: [`unset_time_limit_sec`](@ref), [`time_limit_sec`](@ref).

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> time_limit_sec(model)

julia> set_time_limit_sec(model, 60.0)

julia> time_limit_sec(model)
60.0

julia> unset_time_limit_sec(model)

julia> time_limit_sec(model)
```
