```Julia
slinchmole(U::UnitSystem) = molaramount(𝟏,U,IPS)
```

分子の `molaramount` 単位 (mol または lb-mol)。

```Julia
julia> slinchmole(Metric) # mol
175126.83524647632

julia> slinchmole(English) # lb-mol
386.0885826771652

julia> slinchmole(British) # slug-mol
11.999999999999998
```
