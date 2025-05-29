```
getoffset(UT1, TAI, second, fraction[, eop])
```

Return the offset between [`UT1`](@ref) and [`TAI`](@ref) for the current epoch (`second` after J2000 and `fraction`) in seconds. Optionally, a custom Earth orientation data struct `eop` can be provided, see [EarthOrientation.jl](https://github.com/JuliaAstro/EarthOrientation.jl).

# Example

```jldoctest; setup = :(using AstroTime; AstroTime.load_test_eop())
julia> getoffset(UT1, TAI, 0, 0.0)
31.644974965344606
```
