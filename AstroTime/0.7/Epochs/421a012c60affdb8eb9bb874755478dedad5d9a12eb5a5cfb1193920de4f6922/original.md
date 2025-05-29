```
julian_period([T,] ep::Epoch; origin=:j2000, scale=timescale(ep), unit=days)
```

Return the period since Julian Epoch `origin` within the time scale `scale` expressed in `unit` for a given epoch `ep`. The result is an [`AstroPeriod`](@ref) object by default. If the type argument `T` is present, the result is converted to `T` instead.

### Example

```jldoctest; setup = :(using AstroTime)
julia> ep = TAIEpoch(2018, 2, 6, 20, 45, 0.0)
2018-02-06T20:45:00.000 TAI

julia> julian_period(ep; scale=TT)
6611.364955833334 days

julia> julian_period(ep; unit=years)
18.100929728496464 years

julia> julian_period(Float64, ep)
6611.364583333333
```
