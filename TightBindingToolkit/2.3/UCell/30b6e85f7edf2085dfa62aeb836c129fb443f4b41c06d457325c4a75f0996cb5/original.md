```julia
GetDistance(uc::UnitCell, base::Int64, target::Int64, offset::Vector{Int64}) --> Float64
```

get the distance between site at position (0, `base`) and (R, `target`), where R = `offset`, when written in units of the unit cell primitive vectors.
