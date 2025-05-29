```
function dselect(dInfo::Dinfo,
    currentColnames::Vector{String}, selectColnames::Vector{String};
    tgt=dInfo.val)::Dinfo
```

Convenience overload of `dselect` that works with column names.
