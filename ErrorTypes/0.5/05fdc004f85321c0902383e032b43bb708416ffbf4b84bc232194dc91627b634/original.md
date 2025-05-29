```
map_or(f, x::Result, v)
```

If `x` is a result value, return `f(unwrap(x))`. Else, return `v`.

See also: [`unwrap_or`](@ref), [`and_then`](@ref)

# Examples

```jldoctest
julia> map_or(isodd, some(9), nothing)
true

julia> map_or(isodd, none(Int), nothing) === nothing
true

julia> map_or(ncodeunits, none(String), 0)
0
```
