```
set_start_value(variable::GenericVariableRef, value::Union{Real,Nothing})
```

`variable`の開始値（[`MOI.VariablePrimalStart`](@ref)）を`value`に設定します。

開始値を解除するには`nothing`を渡します。

注意: `VariablePrimalStart`は時々「MIP-starts」または「warmstarts」と呼ばれます。

関連情報: [`has_start_value`](@ref), [`start_value`](@ref).

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, start = 1.5);

julia> @variable(model, y);

julia> has_start_value(x)
true

julia> has_start_value(y)
false

julia> start_value(x)
1.5

julia> set_start_value(x, nothing)

julia> has_start_value(x)
false

julia> set_start_value(y, 2.0)

julia> has_start_value(y)
true

julia> start_value(y)
2.0
```
