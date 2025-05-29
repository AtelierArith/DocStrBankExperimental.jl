```Julia
poundmole(U::UnitSystem) = molaramount(𝟏,U,English)
```

分子の `molaramount` 単位 (mol または lb-mol)。

```Julia
julia> poundmole(Metric) # mol
453.59237

julia> poundmole(English) # lb-mol
1

julia> poundmole(British) # slug-mol
0.031080950171567256
```
