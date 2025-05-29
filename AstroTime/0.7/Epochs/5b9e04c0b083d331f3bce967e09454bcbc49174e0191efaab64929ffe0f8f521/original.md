```
getoffset(TT, TCG, second, fraction)
```

Return the linear offset between [`TT`](@ref) and [`TCG`](@ref) for the current epoch (`second` after J2000 and `fraction`) in seconds.

# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TT, TCG, 0, 0.0)
0.5058332860211293
```
