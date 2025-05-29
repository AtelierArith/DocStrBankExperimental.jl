```
IntegerRef(v::GenericVariableRef)
```

Return a constraint reference to the constraint constraining `v` to be integer.

Errors if one does not exist.

See also [`is_integer`](@ref), [`set_integer`](@ref), [`unset_integer`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, Int);

julia> IntegerRef(x)
x integer
```
