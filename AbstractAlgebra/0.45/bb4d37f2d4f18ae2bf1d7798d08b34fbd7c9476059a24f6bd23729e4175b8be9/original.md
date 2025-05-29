```
AbstractAlgebra.set_verbosity_level(s::Symbol, l::Int) -> Int
```

If `s` represents a known verbosity scope, set the current verbosity level of `s` to `l`.

One can access the current verbosity level of `s` by calling the function [`get_verbosity_level`](@ref).

If `s` is not yet known as a verbosity scope, the function raises an `ErrorException` showing the error message "Not a valid symbol". One can add `s` to the list of verbosity scopes by calling the function [`add_verbosity_scope`](@ref).

# Examples

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:MyScope)

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 4)
4

julia> AbstractAlgebra.set_verbosity_level(:MyScope, 0)
0
```
