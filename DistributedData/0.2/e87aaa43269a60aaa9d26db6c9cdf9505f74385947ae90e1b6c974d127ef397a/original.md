```
dcount_buckets(ncats::Int, dInfo::Dinfo, nbuckets::Int, buckets::Dinfo)::Matrix{Int}
```

Same as `dcount`, but counts the items in `dInfo` bucketed by `buckets` to produce a matrix of counts, with `ncats` rows and `nbuckets` columns.

Useful with `distributeFCSFileVector` to determine cluster distribution within files.
