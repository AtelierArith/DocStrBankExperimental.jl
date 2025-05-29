```
getoffset(TAI, UT1, second, fraction[, eop])
```

Return the offset between [`TAI`](@ref) and [`UT1`](@ref) for the current epoch (`second` after J2000 and `fraction`) in seconds. Optionally, a custom Earth orientation data struct `eop` can be provided, see [EarthOrientation.jl](https://github.com/JuliaAstro/EarthOrientation.jl).

# Example

```jldoctest; setup = :(using AstroTime; AstroTime.load_test_eop())
julia> getoffset(TAI, UT1, 0, 0.0)
-31.644974644349812
```
