```julia
GetAllOffsets(OffsetRange::Int64, dim::Int64) --> Vector{Vector{Int64}}
```

Given a range, returns the set of all possible Bond offsets such that each element of the offset vector lies in [-`OffsetRange`, `OffsetRange`].
