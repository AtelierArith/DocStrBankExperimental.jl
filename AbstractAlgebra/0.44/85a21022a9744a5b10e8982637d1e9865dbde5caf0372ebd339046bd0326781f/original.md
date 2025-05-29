```
AbstractAlgebra.get_verbosity_level(s::Symbol) -> Int
```

If `s` represents a known verbosity scope, return the current verbosity level of `s`.

One can modify the current verbosity level of `s` by calling the function [`set_verbosity_level`](@ref).

If `s` is not yet known as a verbosity scope, the function raises an `ErrorException` showing the error message "Not a valid symbol". One can add `s` to the list of verbosity scopes by calling the function [`add_verbosity_scope`](@ref).

# Examples

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:MyScope)

julia> AbstractAlgebra.get_verbosity_level(:MyScope)
0

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 4)
4

julia> AbstractAlgebra.get_verbosity_level(:MyScope)
4

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 0)
0

julia> AbstractAlgebra.get_verbosity_level(:MyScope)
0
```
