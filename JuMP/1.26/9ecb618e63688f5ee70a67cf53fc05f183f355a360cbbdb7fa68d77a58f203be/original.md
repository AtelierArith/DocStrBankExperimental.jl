```
delete_lower_bound(v::GenericVariableRef)
```

Delete the lower bound constraint of a variable.

See also [`LowerBoundRef`](@ref), [`has_lower_bound`](@ref), [`lower_bound`](@ref), [`set_lower_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> has_lower_bound(x)
true

julia> delete_lower_bound(x)

julia> has_lower_bound(x)
false
```
