```Julia
slugmole(U::UnitSystem) = molaramount(𝟏,U,British)
```

分子 `molaramount` 単位 (mol または lb-mol)。

```Julia
julia> slugmole(Metric) # mol
14593.902937206363

julia> slugmole(English) # lb-mol
32.17404855643044

julia> slugmole(British) # slug-mol
1
```
