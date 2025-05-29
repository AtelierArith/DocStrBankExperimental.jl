```
AstroPeriod{U, T}(unit, Δt) where {U<:TimeUnit, T}
```

An `AstroPeriod` object represents a time interval of `Δt` with a [`TimeUnit`](@ref) of `unit`.  Periods should be constructed via the shorthand syntax shown in the examples below.

### Examples

```jldoctest; setup = :(using AstroTime)
julia> 3.0seconds
3.0 seconds

julia> 1.0minutes
1.0 minutes

julia> 12hours
12.0 hours

julia> days_per_year = 365
365
julia> days_per_year * days
365.0 days

julia> 10.0years
10.0 years

julia> 1centuries
1.0 centuries
```
