```
BinaryRef(v::GenericVariableRef)
```

Return a constraint reference to the constraint constraining `v` to be binary. Errors if one does not exist.

See also [`is_binary`](@ref), [`set_binary`](@ref), [`unset_binary`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin);

julia> BinaryRef(x)
x binary
```
