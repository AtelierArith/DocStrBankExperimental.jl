```
extractsat(files::AbstractVector{String}, var::String, cid::Int)
```

Multi-threaded extraction of `var` at a fixed cell ID `cid` from `files`. This assumes that `files` come from the same grid structure.
