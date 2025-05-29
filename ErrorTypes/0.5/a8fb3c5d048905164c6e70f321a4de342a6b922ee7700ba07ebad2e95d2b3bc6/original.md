```
unwrap_error_or(x::Result, v)
```

Like `unwrap_or`, but unwraps an error.

See also: [`unwrap_or`](@ref)

# Examples

```jldoctest
julia> unwrap_error_or(Result{Int, String}(Err("abc")), 19)
"abc"

julia> unwrap_error_or(none(String), "error") === nothing
true

julia> unwrap_error_or(some([1, 2, 3]), Int32[])
Int32[]
```
