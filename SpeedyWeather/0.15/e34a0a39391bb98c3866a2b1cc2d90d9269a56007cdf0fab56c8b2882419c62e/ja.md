```julia
struct Earth<:AbstractPlanet
    rotation::AbstractFloat
    gravity::AbstractFloat
    daily_cycle::Bool
    length_of_day::Dates.Second
    seasonal_cycle::Bool
    length_of_year::Dates.Second
    equinox::Dates.DateTime
    axial_tilt::AbstractFloat
    solar_constant::AbstractFloat
end
```
