```
Option{T}
```

Alias for `Result{T, Nothing}`. Useful when the error type of a `Result` need not store any information. Construct value instances with `some(x)` and error instances with `none(::Type)`.

See also: [`Result`](@ref)

# Examples

```jldoctest
julia> some(4) isa Option{Int}
true

julia> is_error(some(4))
false

julia> none(String) isa Option{String} && is_error(none(String))
true
```
