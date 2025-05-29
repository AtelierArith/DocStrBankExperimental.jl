```
has_start_value(variable::AbstractVariableRef)
```

Return `true` if the variable has a start value set, otherwise return `false`.

See also: [`start_value`](@ref), [`set_start_value`](@ref).

## Example

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
