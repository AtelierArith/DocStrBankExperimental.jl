```Julia
luminousintensity(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)/solidangle(U,S)
luminousintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousintensity(U,S)
```

光の知覚された力または `luminousintensity` (cd, lm⋅rad⁻²)、単位変換係数。
