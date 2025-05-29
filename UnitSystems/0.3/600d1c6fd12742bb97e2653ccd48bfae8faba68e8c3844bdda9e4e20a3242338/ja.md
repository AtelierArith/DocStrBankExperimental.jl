```Julia
molarvolume(U::UnitSystem,S::UnitSystem) = volume(U,S)/molaramount(U,S)
molarvolume(v::Real,U::UnitSystem,S::UnitSystem) = v/molarvolume(U,S)
```

占有された `volume` あたりの `molaramount` または `molarvolume` (m³⋅mol⁻¹)、単位換算係数。

```Julia
julia> molarvolume(CGS,Metric) # m³⋅cm⁻³
1.0000000000000006e-6

julia> molarvolume(English,SI2019) # m³⋅ft⁻³
6.242796055468538e-5
```
