```
ParameterRef(x::GenericVariableRef)
```

Return a constraint reference to the constraint constraining `x` to be a parameter.

Errors if one does not exist.

See also [`is_parameter`](@ref), [`set_parameter_value`](@ref), [`parameter_value`](@ref).

## Example

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
