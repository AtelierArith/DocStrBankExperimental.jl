```
time_limit_sec(model::GenericModel)
```

`model`の時間制限（秒単位）を返します。

設定されていない場合は`nothing`を返します。

関連: [`set_time_limit_sec`](@ref), [`unset_time_limit_sec`](@ref).

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
