```
getoffset(TT, TAI, args...)
```

Return the fixed offset between [`TT`](@ref) and [`TAI`](@ref) in seconds.

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TT, TAI)
-32.184
```
