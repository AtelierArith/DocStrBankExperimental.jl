```
Epoch(ep::Epoch{S1}, scale::S2) where {S1, S2}
```

Convert `ep`, an `Epoch` with time scale `S1`, to an `Epoch` with time scale `S2`.

### Examples

```jldoctest; setup = :(using AstroTime)
julia> ep = TTEpoch(2000,1,1)
2000-01-01T00:00:00.000 TT

julia> Epoch(ep, TAI)
1999-12-31T23:59:27.816 TAI
```
