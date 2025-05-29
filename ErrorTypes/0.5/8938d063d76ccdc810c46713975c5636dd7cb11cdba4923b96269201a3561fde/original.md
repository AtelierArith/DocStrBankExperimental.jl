```
expect_error(x::Result, s::AbstractString)
```

If `x` contains an `Err`, return the content of the `Err`. Else, throw an error with message `s`.

See also: [`unwrap_error`](@ref), [`expect`](@ref)

# Examples

```jldoctest
julia> expect_error(none(Int), "expected none") === nothing
true

julia> expect_error(Result{Vector, String}(Err("Mistake!")), "must be error")
"Mistake!"

julia> expect_error(some(3), "must be none")
ERROR: must be none
[...]
```
