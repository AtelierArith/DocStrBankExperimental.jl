```
unwrap_or_else(f, x::Result)
```

If `x` is an error value, return `f(unwrap_error(x))`. Else, unwrap `x` and return its content.

See also: [`unwrap_error_or_else`](@ref), [`unwrap_or`](@ref)

# Examples

```jldoctest
julia> unwrap_or_else(isnothing, some(3))
3

julia> unwrap_or_else(println, none(Int))
nothing

julia> unwrap_or_else(ncodeunits, Result{Int, String}(Err("my_error")))
8
```
