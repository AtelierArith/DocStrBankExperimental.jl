```
namedtuple(lineage::Lineage; kwargs...)
```

Return a NamedTuple whose filednames is ranks (in the `CanonicalRanks`) of the `lineage`. This function is useful for converting `Lineage` to `DataFrame`, for example.

# Arguments

  * `fill_by_missing::Bool = false` - If `true`, fills missing instead of `UnclassifiedTaxon`.
