```
is_error(x::Result)
```

Check if `x` contains an error value.

See also: [`Result`](@ref), [`Option`](@ref)

# Examples

```jldoctest
julia> is_error(none(Int)), is_error(some(5))
(true, false)
```
