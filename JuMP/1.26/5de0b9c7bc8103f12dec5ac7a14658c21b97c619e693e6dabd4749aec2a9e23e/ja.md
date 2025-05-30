```
ParameterRef(x::GenericVariableRef)
```

`x`をパラメータとして制約する制約参照を返します。

存在しない場合はエラーになります。

[`is_parameter`](@ref)、[`set_parameter_value`](@ref)、[`parameter_value`](@ref)も参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, p in Parameter(2))
p

julia> ParameterRef(p)
p ∈ MathOptInterface.Parameter{Float64}(2.0)

julia> @variable(model, x);

julia> ParameterRef(x)
ERROR: Variable x is not a parameter.
Stacktrace:
[...]
```
