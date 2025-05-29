```Julia
molargas(U::UnitSystem) = boltzmann(x)*avogadro(x)
```

普遍気体定数 `Rᵤ` は特定の `gasconstant(x)*molarmass(x)` 値に分解されます。

```Julia
julia> molargas(SI2019) # J⋅K⁻¹⋅mol⁻¹
8.31446261815324

julia> molargas(English)/𝟐^4/𝟑^2 # psi⋅ft³⋅°R⁻¹⋅lb-mol⁻¹
10.731577089016291

julia> molargas(English)/atmosphere(English) # atm⋅ft³⋅R⁻¹⋅lb-mol⁻¹
0.7302405072952732

julia> molargas(English)/thermalunit(English) # BTU⋅°R⁻¹⋅lb-mol⁻¹
1.9859050081929637

julia> molargas(Metric)/atmosphere(Metric) # atm⋅m³⋅K⁻¹⋅mol⁻¹
8.20573660809597e-5

julia> molargas(Metric)/torr(Metric) # m³⋅torr⋅K⁻¹⋅mol⁻¹
0.06236359822152937

julia> molargas(English)/torr(English) # ft³⋅torr⋅°R⁻¹⋅lb-mol⁻¹
554.9827855444076

julia> molargas(CGS) # erg⋅K⁻¹⋅mol⁻¹
8.314462618153238e7

julia> molargas(English) # ft⋅lb⋅°R⁻¹⋅lb-mol⁻¹
1545.3471008183458

julia> molargas(British) # ft⋅lb⋅°R⁻¹⋅slug-mol⁻¹
49720.072658268466

julia> molargas(SI1976) # J⋅K⁻¹⋅mol⁻¹ (US1976 Standard Atmosphere)
8.314320000000002
```
