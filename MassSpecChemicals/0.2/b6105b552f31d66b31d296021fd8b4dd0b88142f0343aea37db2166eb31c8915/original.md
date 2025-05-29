```
chemicalsmiles(chemical::AbstractChemical; kwargs...)
```

Get SMILES of `chemical`. It is equivalent to `getchemicalattr(chemical, :SMILES; kwargs...)` except that it returns `""` when SMILES is not available.
