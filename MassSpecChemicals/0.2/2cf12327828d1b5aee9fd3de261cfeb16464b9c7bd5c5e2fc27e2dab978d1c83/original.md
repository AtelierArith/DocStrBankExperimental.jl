```
chemicalformula(chemical::AbstractChemical; kwargs...)
```

Get formula of `chemical`. It is equivalent to `getchemicalattr(chemical, :formula; kwargs...)` except that it returns `""` when formula is not available.
