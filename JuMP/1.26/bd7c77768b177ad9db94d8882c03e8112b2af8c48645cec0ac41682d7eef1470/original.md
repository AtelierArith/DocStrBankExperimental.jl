```
delete_upper_bound(v::GenericVariableRef)
```

Delete the upper bound constraint of a variable.

Errors if one does not exist.

See also [`UpperBoundRef`](@ref), [`has_upper_bound`](@ref), [`upper_bound`](@ref), [`set_upper_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> has_upper_bound(x)
true

julia> delete_upper_bound(x)

julia> has_upper_bound(x)
false
```
