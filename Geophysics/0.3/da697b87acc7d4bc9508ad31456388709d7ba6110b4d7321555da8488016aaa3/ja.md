```
mass(P::Planet,U::UnitSystem) = gravitation(P,U)/newton(U)
```

天体 `Planet` の慣性 `mass` (kg)。

```Julia
julia> mass(Earth) # kg
5.972166613228325e24
```
