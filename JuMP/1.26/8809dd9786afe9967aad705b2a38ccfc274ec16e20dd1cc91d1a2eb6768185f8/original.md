```
UpperBoundRef(v::GenericVariableRef)
```

Return a constraint reference to the upper bound constraint of `v`.

Errors if one does not exist.

See also [`has_upper_bound`](@ref), [`upper_bound`](@ref), [`set_upper_bound`](@ref), [`delete_upper_bound`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x <= 1.0);

julia> UpperBoundRef(x)
x ≤ 1
```
