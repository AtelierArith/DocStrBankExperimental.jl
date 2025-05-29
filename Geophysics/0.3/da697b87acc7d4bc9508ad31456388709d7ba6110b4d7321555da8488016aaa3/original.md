```
mass(P::Planet,U::UnitSystem) = gravitation(P,U)/newton(U)
```

Inertial `mass` of a celestial `Planet` body (kg).

```Julia
julia> mass(Earth) # kg
5.972166613228325e24
```
