```
FixRef(v::GenericVariableRef)
```

Return a constraint reference to the constraint fixing the value of `v`.

Errors if one does not exist.

See also [`is_fixed`](@ref), [`fix_value`](@ref), [`fix`](@ref), [`unfix`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x == 1);

julia> FixRef(x)
x = 1
```
