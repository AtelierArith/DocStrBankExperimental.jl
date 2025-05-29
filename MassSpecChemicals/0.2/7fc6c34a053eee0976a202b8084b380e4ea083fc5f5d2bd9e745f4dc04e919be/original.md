```
rt(chemical::AbstractChemical; kwargs...)
```

Get retention time of `chemical`. It is equivalent to `getchemicalattr(chemical, :rt; kwargs...)` except that it returns `NaN` when rt is not available.
