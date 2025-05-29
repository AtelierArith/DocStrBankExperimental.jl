```
siteinds(M::Union{MPS, MPO}}, j::Integer; kwargs...)
```

Return the site Indices found of the MPO or MPO at the site `j` as an IndexSet.

Optionally filter prime tags and prime levels with keyword arguments like `plev` and `tags`.
