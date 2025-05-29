```
calculateAGIC(Ns::AbstractVector{HybridNetwork})
```

Calculates the **A**verage **G**ene tree **I**nternode **C**ounts for all pairs of taxa across all networks in `Ns`. If `allow_missing_pairs` is false, an error will be thrown if there are pairs of taxa that never appear in `Ns` together. Otherwise, entries for taxa that never appear together will be set to `default_missing_value`.

# Returns

1. AGIC matrix
2. names of taxa corresponding to rows/columns in the AGID matrix
