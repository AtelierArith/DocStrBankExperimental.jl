```
set_parameter_value(x::GenericVariableRef, value)
```

変数 `x` のパラメータ制約を `value` に更新します。

`x` がパラメータでない場合はエラーが発生します。

関連情報としては [`ParameterRef`](@ref)、[`is_parameter`](@ref)、[`parameter_value`](@ref) があります。

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
