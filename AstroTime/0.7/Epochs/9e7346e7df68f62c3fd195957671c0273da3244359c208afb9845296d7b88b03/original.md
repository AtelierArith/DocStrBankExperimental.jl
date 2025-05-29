```
getoffset(TCB, TDB, second, fraction)
```

Return the linear offset between [`TCB`](@ref) and [`TDB`](@ref) for the current epoch (`second` after J2000 and `fraction`) in seconds.

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TCB, TDB, 0, 0.0)
-11.253721593757295
```
