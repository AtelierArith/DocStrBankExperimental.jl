```
gravitation(P::Planet,U::UnitSystem) = mass(P)*gravitation(U)
```

天体 `Planet` の標準 `gravitation` パラメータ (m³⋅s⁻²)。

```Julia
julia> gravitation(Earth) # m³⋅s⁻²
3.986004418e14
```
