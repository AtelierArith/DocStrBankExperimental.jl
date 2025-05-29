```
julian_twopart(ep)
```

Return the two-part Julian Date for epoch `ep`, which is a tuple consisting of the Julian day number and the fraction of the day.

### Example

```jldoctest; setup = :(using AstroTime)
julia> julian_twopart(TAIEpoch(2000, 1, 2))
(2.451545e6 days, 0.5 days)
```
