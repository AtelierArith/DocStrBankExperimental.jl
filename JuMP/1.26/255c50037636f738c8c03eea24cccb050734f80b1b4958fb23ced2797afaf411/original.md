```
upper_bound(v::GenericVariableRef)
```

Return the upper bound of a variable.

Error if one does not exist.

See also [`UpperBoundRef`](@ref), [`has_upper_bound`](@ref), [`set_upper_bound`](@ref), [`delete_upper_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> upper_bound(x)
1.0
```
