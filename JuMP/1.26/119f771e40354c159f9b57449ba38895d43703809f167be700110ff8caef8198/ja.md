```
set_upper_bound(v::GenericVariableRef, upper::Number)
```

変数の上限を設定します。存在しない場合は、上限制約を作成します。

関連情報としては、[`UpperBoundRef`](@ref)、[`has_upper_bound`](@ref)、[`upper_bound`](@ref)、[`delete_upper_bound`](@ref)があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> upper_bound(x)
1.0

julia> set_upper_bound(x, 2.0)

julia> upper_bound(x)
2.0
```
