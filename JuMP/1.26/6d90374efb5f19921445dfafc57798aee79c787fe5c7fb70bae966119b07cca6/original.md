```
unset_binary(variable_ref::GenericVariableRef)
```

Remove the binary constraint on the variable `variable_ref`.

See also [`BinaryRef`](@ref), [`is_binary`](@ref), [`set_binary`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin);

julia> is_binary(x)
true

julia> unset_binary(x)

julia> is_binary(x)
false
```
