```
lower_bound(v::GenericVariableRef)
```

Return the lower bound of a variable. Error if one does not exist.

See also [`LowerBoundRef`](@ref), [`has_lower_bound`](@ref), [`set_lower_bound`](@ref), [`delete_lower_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> lower_bound(x)
1.0
```
