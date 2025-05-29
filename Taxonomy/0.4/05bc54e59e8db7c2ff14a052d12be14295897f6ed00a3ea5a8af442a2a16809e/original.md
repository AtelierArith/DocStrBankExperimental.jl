```
reformat(l::Lineage, ranks::Vector{Symbol})
```

Return the `Lineage` object reformatted according to the given ranks. If there is no corresponding taxon in the lineage to the rank, `UnclassifiedTaxon` will be stored. Once a `Lineage` is reformatted, it cannot be reformatted again.
