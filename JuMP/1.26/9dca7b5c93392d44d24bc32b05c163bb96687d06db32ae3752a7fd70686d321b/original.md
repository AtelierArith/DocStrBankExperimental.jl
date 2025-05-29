```
fix_value(v::GenericVariableRef)
```

Return the value to which a variable is fixed.

Error if one does not exist.

See also [`FixRef`](@ref), [`is_fixed`](@ref), [`fix`](@ref), [`unfix`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x == 1);

julia> fix_value(x)
1.0
```
