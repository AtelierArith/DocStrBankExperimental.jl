```
getoffset(TAI, TT, args...)
```

Return the fixed offset between [`TAI`](@ref) and [`TT`](@ref) in seconds.

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TAI, TT)
32.184
```
