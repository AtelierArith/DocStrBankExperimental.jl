```
parameter_value(x::GenericVariableRef)
```

Return the value of the parameter `x`.

Errors if `x` is not a parameter.

See also [`ParameterRef`](@ref), [`is_parameter`](@ref), [`set_parameter_value`](@ref).

## Example

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
