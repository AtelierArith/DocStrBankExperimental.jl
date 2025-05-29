```
unwrap(x::Result)
```

If `x` is of the associated error type, throw an error. Else, return the contained result type.

See also: [`unwrap_error`](@ref), [`@unwrap_or`](@ref)

# Examples

```jldoctest
julia> unwrap(some(Any[]))
Any[]

julia> unwrap(none(Int))
ERROR: unwrap on unexpected type
[...]

julia> unwrap(Result{String, Int32}(Ok("Lin Wei")))
"Lin Wei"
```
