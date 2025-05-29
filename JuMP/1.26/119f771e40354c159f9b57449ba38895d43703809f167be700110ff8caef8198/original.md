```
set_upper_bound(v::GenericVariableRef, upper::Number)
```

Set the upper bound of a variable. If one does not exist, create an upper bound constraint.

See also [`UpperBoundRef`](@ref), [`has_upper_bound`](@ref), [`upper_bound`](@ref), [`delete_upper_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> upper_bound(x)
1.0

julia> set_upper_bound(x, 2.0)

julia> upper_bound(x)
2.0
```
