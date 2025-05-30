```
FixRef(v::GenericVariableRef)
```

値 `v` を固定する制約への参照を返します。

存在しない場合はエラーになります。

関連項目としては [`is_fixed`](@ref), [`fix_value`](@ref), [`fix`](@ref), [`unfix`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x == 1);

julia> FixRef(x)
x = 1
```
