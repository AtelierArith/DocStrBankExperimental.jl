```
has_lower_bound(v::GenericVariableRef)
```

Return `true` if `v` has a lower bound. If `true`, the lower bound can be queried with [`lower_bound`](@ref).

See also [`LowerBoundRef`](@ref), [`lower_bound`](@ref), [`set_lower_bound`](@ref), [`delete_lower_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> has_lower_bound(x)
true
```
