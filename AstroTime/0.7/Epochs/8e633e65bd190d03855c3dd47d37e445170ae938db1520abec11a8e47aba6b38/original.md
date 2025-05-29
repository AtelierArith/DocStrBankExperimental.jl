```
getoffset(ep::Epoch, scale::TimeScale)
```

For a given epoch `ep` return the offset between its time scale and another time `scale` in seconds.

# Example

```jldoctest; setup = :(using AstroTime)
julia> tai = TAIEpoch(2000, 1, 1)
2000-01-01T00:00:00.000 TAI

julia> getoffset(tai, TT)
32.184
```
