```Julia
luminousflux(U::UnitSystem,S::UnitSystem) = luminousenergy(U,S)*frequency(U,S)
luminousflux(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousflux(U,S)
```

光の知覚パワーまたは `luminousflux` (lm, cd⋅rad⋅²)、単位変換係数。
