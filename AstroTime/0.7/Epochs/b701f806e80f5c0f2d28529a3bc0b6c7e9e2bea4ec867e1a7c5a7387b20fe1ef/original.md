```
getoffset(TCG, TT, second, fraction)
```

Return the linear offset between [`TCG`](@ref) and [`TT`](@ref) for the current epoch (`second` after J2000 and `fraction`) in seconds.

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TCG, TT, 0, 0.0)
-0.5058332856685995
```
