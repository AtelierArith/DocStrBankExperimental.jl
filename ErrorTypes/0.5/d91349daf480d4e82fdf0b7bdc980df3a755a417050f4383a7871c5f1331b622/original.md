```
unwrap_or(x::Result, v)
```

If `x` is an error value, return `v`. Else, unwrap `x` and return its content.

See also: [`unwrap`](@ref), [`@unwrap_or`](@ref)

# Examples:

```jldoctest
julia> unwrap_or(some(5), 9)
5

julia> unwrap_or(none(Float32), "something else")
"something else"

julia> unwrap_or(Result{Int8, Vector}(Err([])), 0x01)
0x01
```
