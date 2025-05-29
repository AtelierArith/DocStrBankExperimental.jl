```Julia
mole(U::UnitSystem) = molaramount(𝟏,U,Metric)
```

Molecular `molaramount` unit (mol or lb-mol).

```Julia
julia> mole(Metric) # mol
1

julia> mole(English) # lb-mol
0.002204622621848776

julia> mole(British) # slug-mol
6.852176585679177e-5
```
