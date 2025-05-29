```
set_lower_bound(v::GenericVariableRef, lower::Number)
```

変数の下限を設定します。存在しない場合は、新しい下限制約を作成します。

関連情報としては、[`LowerBoundRef`](@ref)、[`has_lower_bound`](@ref)、[`lower_bound`](@ref)、[`delete_lower_bound`](@ref)があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> lower_bound(x)
1.0

julia> set_lower_bound(x, 2.0)

julia> lower_bound(x)
2.0
```
