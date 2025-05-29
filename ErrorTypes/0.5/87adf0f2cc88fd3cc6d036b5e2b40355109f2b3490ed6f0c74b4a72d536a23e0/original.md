```
unwrap_error_or(f, x::Result
```

Returns the wrapped error value if `x` is an error, else return `f(unwrap(x))`.

See also: [`@unwrap_error_or`](@ref), [`unwrap_or_else`](@ref)

# Examples

```jldoctest
julia> unwrap_error_or_else(ncodeunits, some("abc"))
3

julia> unwrap_error_or_else(ncodeunits, none(String)) === nothing
true

julia> unwrap_error_or_else(n -> n + 1, Result{Int, String}(Err("abc")))
"abc"
```
