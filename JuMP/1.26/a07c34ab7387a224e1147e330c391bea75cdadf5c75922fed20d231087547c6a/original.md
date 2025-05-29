```
set_start_value(variable::GenericVariableRef, value::Union{Real,Nothing})
```

Set the start value ([`MOI.VariablePrimalStart`](@ref)) of the `variable` to `value`.

Pass `nothing` to unset the start value.

Note: `VariablePrimalStart`s are sometimes called "MIP-starts" or "warmstarts".

See also: [`has_start_value`](@ref), [`start_value`](@ref).

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

julia> set_start_value(x, nothing)

julia> has_start_value(x)
false

julia> set_start_value(y, 2.0)

julia> has_start_value(y)
true

julia> start_value(y)
2.0
```
