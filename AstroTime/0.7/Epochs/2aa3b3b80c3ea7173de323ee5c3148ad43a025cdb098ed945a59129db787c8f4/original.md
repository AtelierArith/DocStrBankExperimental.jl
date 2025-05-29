```
Epoch{S}(Δtai, ep::TAIEpoch) where S
```

Convert `ep`, a `TAIEpoch`, to an `Epoch` with time scale `S` by overriding the offset between `S2` and `TAI` with `Δtai`.

### Examples

```jldoctest; setup = :(using AstroTime)
julia> ep = TAIEpoch(2000,1,1)
2000-01-01T00:00:00.000 TAI

julia> TTEpoch(32.184, ep)
2000-01-01T00:00:32.184 TT
```
