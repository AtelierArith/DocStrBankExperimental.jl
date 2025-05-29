```
dstat_buckets(dInfo::Dinfo, nbuckets::Int, buckets::Dinfo, columns::Vector{Int})::Tuple{Matrix{Float64}, Matrix{Float64}}
```

A version of `dstat` that works with bucketing information (e.g. clusters); returns a tuple of matrices.
