```
unfix(v::GenericVariableRef)
```

Delete the fixing constraint of a variable.

Error if one does not exist.

See also [`FixRef`](@ref), [`is_fixed`](@ref), [`fix_value`](@ref), [`fix`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x == 1);

julia> is_fixed(x)
true

julia> unfix(x)

julia> is_fixed(x)
false
```
