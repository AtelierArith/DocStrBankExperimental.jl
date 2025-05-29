```
unfix(v::GenericVariableRef)
```

変数の固定制約を削除します。

存在しない場合はエラーになります。

関連項目としては [`FixRef`](@ref)、[`is_fixed`](@ref)、[`fix_value`](@ref)、[`fix`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x == 1);

julia> is_fixed(x)
true

julia> unfix(x)

julia> is_fixed(x)
false
```
