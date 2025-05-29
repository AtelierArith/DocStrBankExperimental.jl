```
modified_julian(ep)
```

Return the Modified Julian Date for epoch `ep`.

### Example

```jldoctest; setup = :(using AstroTime)
julia> modified_julian(TAIEpoch(2000, 1, 1, 12))
51544.5 days
```
