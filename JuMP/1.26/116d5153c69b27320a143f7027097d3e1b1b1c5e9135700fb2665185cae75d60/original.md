```
is_binary(v::GenericVariableRef)
```

Return `true` if `v` is constrained to be binary.

See also [`BinaryRef`](@ref), [`set_binary`](@ref), [`unset_binary`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin);

julia> is_binary(x)
true
```
