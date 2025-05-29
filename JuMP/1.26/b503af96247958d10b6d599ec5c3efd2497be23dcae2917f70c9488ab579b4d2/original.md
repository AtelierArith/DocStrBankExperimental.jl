```
is_fixed(v::GenericVariableRef)
```

Return `true` if `v` is a fixed variable. If `true`, the fixed value can be queried with [`fix_value`](@ref).

See also [`FixRef`](@ref), [`fix_value`](@ref), [`fix`](@ref), [`unfix`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_fixed(x)
false

julia> fix(x, 1.0)

julia> is_fixed(x)
true
```
