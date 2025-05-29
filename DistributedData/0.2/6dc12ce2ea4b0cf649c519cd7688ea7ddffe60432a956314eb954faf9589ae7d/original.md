```
dmedian_buckets(dInfo::Dinfo, nbuckets::Int, buckets::Dinfo, columns::Vector{Int}; iters=20)
```

A version of `dmedian` that works with the bucketing information (i.e. clusters) from `nbuckets` and `buckets`.
