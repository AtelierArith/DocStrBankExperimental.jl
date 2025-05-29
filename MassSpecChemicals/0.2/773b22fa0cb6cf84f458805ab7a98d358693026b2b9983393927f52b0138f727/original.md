```
chemicalelements(chemical::AbstractChemical; kwargs...)
```

Get elements of `chemical`. It is equivalent to `getchemicalattr(chemical, :elements; kwargs...)` except that it returns `Pair{String, Int}[]` when elements are not available.
