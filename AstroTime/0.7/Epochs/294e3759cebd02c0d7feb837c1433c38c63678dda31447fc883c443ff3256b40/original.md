```
getoffset(TDB, TCB, second, fraction)
```

Return the linear offset between [`TDB`](@ref) and [`TCB`](@ref) for the current epoch (`second` after J2000 and `fraction`) in seconds.

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TDB, TCB, 0, 0.0)
11.253721768248475
```
