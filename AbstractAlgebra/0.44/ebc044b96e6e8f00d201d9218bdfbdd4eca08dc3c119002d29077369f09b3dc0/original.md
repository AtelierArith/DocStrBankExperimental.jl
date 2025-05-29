```
AbstractAlgebra.get_assertion_level(s::Symbol) -> Int
```

If `s` represents a symbol of a known assertion scope, return the current assertion level of `s`.

One can modify the current assertion level of `s` by calling the function [`set_assertion_level`](@ref).

If `s` is not yet known as an assertion scope, the function raises an `ErrorException` showing the error message "Not a valid symbol". One can add `s` to the list of assertion scopes by calling the function [`add_assertion_scope`](@ref).

# Examples

```jldoctest
julia> AbstractAlgebra.add_assertion_scope(:MyScope)

julia> AbstractAlgebra.get_assertion_level(:MyScope)
0

julia> AbstractAlgebra.set_assertion_level(:MyScope, 1)
1

julia> AbstractAlgebra.get_assertion_level(:MyScope)
1

julia> AbstractAlgebra.set_assertion_level(:MyScope, 0)
0

julia> AbstractAlgebra.get_assertion_level(:MyScope)
0
```
