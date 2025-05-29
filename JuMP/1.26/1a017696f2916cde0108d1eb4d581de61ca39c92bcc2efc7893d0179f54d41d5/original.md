```
is_parameter(x::GenericVariableRef)::Bool
```

Return `true` if `x` is constrained to be a parameter.

See also [`ParameterRef`](@ref), [`set_parameter_value`](@ref), [`parameter_value`](@ref).

## Example

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
