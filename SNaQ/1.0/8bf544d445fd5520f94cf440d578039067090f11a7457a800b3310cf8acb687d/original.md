```
fittedquartetCF(d::DataCF, format::Symbol)
```

Data frame with the observed and expected quartet concordance factors after estimation of a network with `snaq!`, or fitting of quartet CF data on a fixed network. The format can be `:wide` (default) or `:long`.

  * if `wide`, the output has one row per 4-taxon set, and each row has 10 columns: 4 columns for the taxon names, 3 columns for the observed CFs and 3 columns for the expected CF.
  * if `long`, the output has one row per quartet, i.e. 3 rows per 4-taxon sets, and 7 columns: 4 columns for the taxon names, one column to give the quartet resolution, one column for the observed CF and the last column for the expected CF.

see also: [`topologyQpseudolik!`](@ref) and [`topologymaxQpseudolik!`](@ref) to update the fitted quartet CF expected under a specific network, inside the DataCF object `d`.
