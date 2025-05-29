```
unit(p::AstroPeriod)
```

Return the unit of the period `p`.

### Examples

```jldoctest; setup = :(using AstroTime)
julia> unit(3.0seconds)
AstroTime.Periods.Second()
```
