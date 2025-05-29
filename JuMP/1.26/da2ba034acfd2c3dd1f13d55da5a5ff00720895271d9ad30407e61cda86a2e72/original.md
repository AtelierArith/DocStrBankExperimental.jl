```
is_integer(v::GenericVariableRef)
```

Return `true` if `v` is constrained to be integer.

See also [`IntegerRef`](@ref), [`set_integer`](@ref), [`unset_integer`](@ref).

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
