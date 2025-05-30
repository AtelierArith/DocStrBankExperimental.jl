```
is_fixed(v::GenericVariableRef)
```

`v` が固定変数であれば `true` を返します。`true` の場合、固定値は [`fix_value`](@ref) で照会できます。

関連情報として [`FixRef`](@ref)、[`fix_value`](@ref)、[`fix`](@ref)、[`unfix`](@ref) も参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_fixed(x)
false

julia> fix(x, 1.0)

julia> is_fixed(x)
true
```
