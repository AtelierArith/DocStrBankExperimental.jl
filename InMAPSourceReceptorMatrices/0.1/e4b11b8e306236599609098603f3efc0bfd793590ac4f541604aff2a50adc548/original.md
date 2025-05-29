```
SRM(emis_type) -> srm::Array{Float32, 3}
```

Returns source receptor matrix retrieved from `fs`, with `emis_type` ∈ ("PrimaryPM25", "SOA", "pNO3", "pSO4", "pNH4")

Note that these are huge (52411 x 52411 x 3) and will require ~60-70GB of RAM to hold onto. Index via `(receptor, source, layer)`. Care should be taken if multiple stored in memory.  May take 5-10 minutes to fetch from AWS.

To create a sparse SRM for only a select group of source locations, see [`make_sparse_srm`](@ref).  (that will still call `SRM`, but will call garbage collection before returning the sparse matrix)
