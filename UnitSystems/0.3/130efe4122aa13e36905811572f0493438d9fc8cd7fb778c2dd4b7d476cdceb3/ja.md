```Julia
luminousefficacy(U::UnitSystem,S::UnitSystem) = luminousefficacy(S)/luminousefficacy(U)
luminousefficacy(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousefficacy(U,S)
```

`luminousflux` と `power` または `luminousefficacy` (lm⋅W⁻¹) の比率、単位換算係数。

```Julia
julia> luminousefficacy(CGS,Metric) # erg⋅s⁻¹⋅W⁻¹
1.0e7

julia> luminousefficacy(English,Metric) # ft⋅lb⋅s⁻¹⋅W⁻¹
0.7375621492772654
```
