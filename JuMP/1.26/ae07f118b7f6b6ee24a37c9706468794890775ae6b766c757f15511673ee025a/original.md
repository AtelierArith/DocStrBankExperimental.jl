```
LowerBoundRef(v::GenericVariableRef)
```

Return a constraint reference to the lower bound constraint of `v`.

Errors if one does not exist.

See also [`has_lower_bound`](@ref), [`lower_bound`](@ref), [`set_lower_bound`](@ref), [`delete_lower_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 1.0);

julia> LowerBoundRef(x)
x ≥ 1
```
