```
getcell(meta::MetaVLSV, location:::AbstractVector{<:AbstractFloat}) -> Int
```

Return cell ID containing the given spatial `location` in meter, excluding domain boundaries. Only accept 3D location.
