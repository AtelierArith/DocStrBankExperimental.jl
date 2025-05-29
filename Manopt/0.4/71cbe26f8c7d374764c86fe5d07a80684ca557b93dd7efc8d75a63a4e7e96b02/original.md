```
getindex(r::RecordGroup, s::Symbol)
r[s]
getindex(r::RecordGroup, sT::NTuple{N,Symbol})
r[sT]
getindex(r::RecordGroup, i)
r[i]
```

return an array of recorded values with respect to the `s`, the symbols from the tuple `sT` or the index `i`. See [`get_record`](@ref get_record(r::RecordGroup)) for details.
