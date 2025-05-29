```
julian(ep)
```

Return the Julian Date for epoch `ep`.

### Example

```jldoctest; setup = :(using AstroTime)
julia> julian(TAIEpoch(2000, 1, 1, 12))
2.451545e6 days
```
