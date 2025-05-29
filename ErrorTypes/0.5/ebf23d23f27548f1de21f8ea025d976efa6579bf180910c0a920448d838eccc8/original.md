```
ok(x::Result{T})::Option{T}
```

Construct an `Option` from a `Result`, such that the `Ok` variant becomes a `some`, and the `Err` variant becomes a `none(T)`, discarding the error value if present.

# Examples

```jldoctest
julia> ok(Result{Int32, String}(Err("Some error message")))
none(Int32)

julia> ok(Result{String, Dict}(Ok("Success!")))
some("Success!")

julia> ok(some(5))
some(5)
```
