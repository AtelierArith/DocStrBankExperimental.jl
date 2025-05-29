```
expect(x::Result, s::AbstractString)
```

If `x` is of the associated error type, error with message `s`. Else, return the contained result type.

See also: [`expect_error`](@ref), [`unwrap`](@ref)

# Examples

```jldoctest
julia> expect(some('x'), "cannot be none") === 'x'
true

julia> expect(Result{Int, String}(Ok(19)), "Expected an integer")
19
```
