```Julia
earthradius(U::UnitSystem) = sqrt(earthmass(U)*gravitation(U)/gforce(U))
```

Approximate `length` of standard Earth two-body radius consistent with units (m or ft).

```Julia
julia> earthradius(KKH) # km
6375.416323689185

julia> earthradius(Nautical) # nm
3437.7467707849396

julia> earthradius(IAU) # au
4.2617025856432754e-5
```
