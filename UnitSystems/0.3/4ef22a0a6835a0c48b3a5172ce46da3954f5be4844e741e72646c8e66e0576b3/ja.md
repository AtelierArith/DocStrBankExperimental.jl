```Julia
numberdensity(U::UnitSystem,S::UnitSystem) = 1/volume(U,S)
numberdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/numberdensity(U,S)
```

体積あたりの数または数密度（m⁻³またはft⁻³）、単位変換係数。

```Julia
julia> numberdensity(CGS,Metric) # cm³⋅m⁻³
999999.9999999995

julia> numberdensity(English,Metric) # ft³⋅m⁻³
35.31466672148858
```
