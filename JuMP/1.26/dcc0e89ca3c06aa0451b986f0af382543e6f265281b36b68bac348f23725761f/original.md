```
has_upper_bound(v::GenericVariableRef)
```

Return `true` if `v` has a upper bound. If `true`, the upper bound can be queried with [`upper_bound`](@ref).

See also [`UpperBoundRef`](@ref), [`upper_bound`](@ref), [`set_upper_bound`](@ref), [`delete_upper_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> has_upper_bound(x)
true
```
