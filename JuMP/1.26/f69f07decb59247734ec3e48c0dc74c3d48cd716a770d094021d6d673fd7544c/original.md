```
set_binary(v::GenericVariableRef)
```

Add a constraint on the variable `v` that it must take values in the set $\{0,1\}$.

See also [`BinaryRef`](@ref), [`is_binary`](@ref), [`unset_binary`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_binary(x)
false

julia> set_binary(x)

julia> is_binary(x)
true
```
