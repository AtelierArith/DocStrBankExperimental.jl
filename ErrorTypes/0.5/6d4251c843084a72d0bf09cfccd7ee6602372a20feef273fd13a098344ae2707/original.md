```
and_then(f, ::Type{T}, x::Result{O, E})::Result{T, E}
```

If `is` a result value, return `Result{T, E}(Ok(f(unwrap(x))))`, else return the error value. Always returns a `Result{T, E}`.

**WARNING** If `f(unwrap(x))` is not a `T`, this functions throws an error.

# Examples

```jldoctest
julia> and_then(join, String, some(["ab", "cd"]))
some("abcd")

julia> and_then(i -> Int32(ncodeunits(join(i))), Int32, none(Vector{String}))
none(Int32)
```
