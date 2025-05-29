```
fix_value(v::GenericVariableRef)
```

変数が固定されている値を返します。

存在しない場合はエラーになります。

関連項目としては [`FixRef`](@ref), [`is_fixed`](@ref), [`fix`](@ref), [`unfix`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x == 1);

julia> fix_value(x)
1.0
```
