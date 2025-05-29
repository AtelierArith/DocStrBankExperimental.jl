```Julia
earthradius(U::UnitSystem) = sqrt(earthmass(U)*gravitation(U)/gforce(U))
```

標準的な地球二体半径の近似 `length` は単位（m または ft）に一致します。

```Julia
julia> earthradius(KKH) # km
6375.416323689185

julia> earthradius(Nautical) # nm
3437.7467707849396

julia> earthradius(IAU) # au
4.2617025856432754e-5
```
