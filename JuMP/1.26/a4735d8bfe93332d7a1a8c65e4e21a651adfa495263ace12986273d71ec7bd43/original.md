```
set_lower_bound(v::GenericVariableRef, lower::Number)
```

Set the lower bound of a variable. If one does not exist, create a new lower bound constraint.

See also [`LowerBoundRef`](@ref), [`has_lower_bound`](@ref), [`lower_bound`](@ref), [`delete_lower_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> lower_bound(x)
1.0

julia> set_lower_bound(x, 2.0)

julia> lower_bound(x)
2.0
```
