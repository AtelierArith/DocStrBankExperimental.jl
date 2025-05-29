```Julia
katal(U::UnitSystem) = catalysis(𝟏,U,Metric)
```

`catalysis`のメトリック単位（mol⋅s⁻¹またはlb-mol⋅s⁻¹）。

```Julia
julia> katal(Metric) # mol⋅s⁻¹
1

julia> katal(English) # lb-mol⋅s⁻¹
0.002204622621848776

julia> katal(British) # slug-mol⋅s⁻¹
6.852176585679177e-5
```
