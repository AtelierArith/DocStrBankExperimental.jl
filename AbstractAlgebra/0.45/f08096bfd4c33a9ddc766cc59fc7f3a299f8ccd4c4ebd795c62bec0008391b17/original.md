```
AbstractAlgebra.set_assertion_level(s::Symbol, l::Int) -> Int
```

If `s` represents a known assertion scope, set the current assertion level of `s` to `l`.

One can access the current assertion level of `s` by calling the function [`get_assertion_level`](@ref).

If `s` is not yet known as an assertion scope, the function raises an `ErrorException` showing the error message "Not a valid symbol". One can add `s` to the list of assertion scopes by calling the function [`add_assertion_scope`](@ref).

# Examples

```jldoctest
julia> AbstractAlgebra.add_assertion_scope(:MyScope)

julia> AbstractAlgebra.set_assertion_level(:MyScope, 4)
4

julia> AbstractAlgebra.set_assertion_level(:MyScope, 0)
0
```
