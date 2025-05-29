```
parameter_value(x::GenericVariableRef)
```

パラメータ `x` の値を返します。

`x` がパラメータでない場合はエラーになります。

関連情報としては [`ParameterRef`](@ref), [`is_parameter`](@ref), [`set_parameter_value`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, p in Parameter(2))
p

julia> parameter_value(p)
2.0

julia> set_parameter_value(p, 2.5)

julia> parameter_value(p)
2.5
```
