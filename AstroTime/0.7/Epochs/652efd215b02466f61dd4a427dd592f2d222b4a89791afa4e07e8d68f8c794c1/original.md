```
j2000(ep)
```

Return the J2000 Julian Date for epoch `ep`.

### Example

```jldoctest; setup = :(using AstroTime)
julia> j2000(TAIEpoch(2000, 1, 1, 12))
0.0 days
```
