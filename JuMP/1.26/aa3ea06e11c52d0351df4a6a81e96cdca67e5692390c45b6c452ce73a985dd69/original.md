```
set_integer(variable_ref::GenericVariableRef)
```

Add an integrality constraint on the variable `variable_ref`.

See also [`IntegerRef`](@ref), [`is_integer`](@ref), [`unset_integer`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_integer(x)
false

julia> set_integer(x)

julia> is_integer(x)
true
```
