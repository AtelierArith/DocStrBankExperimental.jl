```Julia
protonmass(U::UnitSystem) = protonunit(U)*dalton(U)
```

サブ原子粒子の陽子質量 `mₚ` は `+𝘦` の基本電荷 (kg または質量) です。

```Julia
julia> protonmass(Metric) # kg
1.6726219236940502e-27

julia> protonmass(SI2019)*lightspeed(SI2019)^2/elementarycharge(SI2019) # eV⋅𝘤⁻²
9.382720881627624e8

julia> protonmass(Metric)/dalton(Metric) # Da
1.007276466621

julia> protonmass(Hartree) # mₑ
1836.152673432705

julia> protonmass(QCD) # mₚ
0.9999999999999999
```
