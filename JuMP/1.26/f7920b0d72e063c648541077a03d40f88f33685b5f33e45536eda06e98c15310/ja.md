```
unset_time_limit_sec(model::GenericModel)
```

ソルバーの時間制限を解除します。

参照: [`set_time_limit_sec`](@ref), [`time_limit_sec`](@ref).

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
