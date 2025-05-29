```
tile(domain::CartesianIndices{N}, fraction::NTuple{N,Int}; cell_based=true) where {N}
```

Split `domain` up by `fraction` into smaller chunks. This is designed to split a CartesianIndex into subdomains.
