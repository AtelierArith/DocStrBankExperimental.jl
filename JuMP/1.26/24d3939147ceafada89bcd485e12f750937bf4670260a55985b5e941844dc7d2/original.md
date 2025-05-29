```
unset_integer(variable_ref::GenericVariableRef)
```

Remove the integrality constraint on the variable `variable_ref`.

Errors if one does not exist.

See also [`IntegerRef`](@ref), [`is_integer`](@ref), [`set_integer`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, Int);

julia> is_integer(x)
true

julia> unset_integer(x)

julia> is_integer(x)
false
```
