```
delete_upper_bound(v::GenericVariableRef)
```

変数の上限制約を削除します。

存在しない場合はエラーになります。

関連項目としては [`UpperBoundRef`](@ref)、[`has_upper_bound`](@ref)、[`upper_bound`](@ref)、[`set_upper_bound`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> has_upper_bound(x)
true

julia> delete_upper_bound(x)

julia> has_upper_bound(x)
false
```
