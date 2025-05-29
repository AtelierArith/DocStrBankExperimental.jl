```
unwrap_error(x::Result)
```

If `x` contains an `Err`, return the content of the `Err`. Else, throw an error.

See also: [`unwrap`](@ref), [`expect_error`](@ref)

# Examples

```jldoctest
julia> unwrap_error(some(3))
ERROR: unwrap on unexpected type
[...]

julia> unwrap_error(none(String)) === nothing
true

julia> unwrap_error(Result{Int, String}(Err("some error")))
"some error"
```
