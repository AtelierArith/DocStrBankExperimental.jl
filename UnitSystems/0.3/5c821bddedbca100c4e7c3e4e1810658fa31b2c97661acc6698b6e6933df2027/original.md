```Julia
earthmole(U::UnitSystem) = molaramount(𝟏,U,Meridian)
```

Molecular `molaramount` unit (mol or lb-mol).

```Julia
julia> earthmole(Metric) # mol
1.0043504565319281

julia> earthmole(English) # lb-mol
0.0022142137367344343

julia> earthmole(British) # slug-mol
6.88198668206427e-5
```
