```
start_value(v::GenericVariableRef)
```

変数 `v` の開始値 ([`MOI.VariablePrimalStart`](@ref)) を返します。

注意: `VariablePrimalStart` は時々「MIP-starts」または「warmstarts」と呼ばれます。

参照: [`has_start_value`](@ref), [`set_start_value`](@ref).

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

julia> set_start_value(y, 2.0)

julia> has_start_value(y)
true

julia> start_value(y)
2.0
```
