```
gravitation(P::Planet,U::UnitSystem) = mass(P)*gravitation(U)
```

Standard `gravitation` parameter for a celestial `Planet` body (m³⋅s⁻²).

```Julia
julia> gravitation(Earth) # m³⋅s⁻²
3.986004418e14
```
