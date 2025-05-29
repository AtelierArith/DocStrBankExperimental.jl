```
is_parameter(x::GenericVariableRef)::Bool
```

`x`がパラメータであることが制約されている場合は`true`を返します。

関連情報としては、[`ParameterRef`](@ref)、[`set_parameter_value`](@ref)、[`parameter_value`](@ref)があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, p in Parameter(2))
p

julia> is_parameter(p)
true

julia> @variable(model, x)
x

julia> is_parameter(x)
false
```
