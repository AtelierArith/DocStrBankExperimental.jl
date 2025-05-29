```
RankineSystem(U::UnitSystem,l,m,g0=𝟏)
```

Constructs new `UnitSystem` from `U` rescaled along `length` and `mass` with optional `gravity` reference constant used to define technical and engineering units.

```Julia
EntropySystem(U,𝟏,l,m,°R,vacuumpermeability(U)/m/l/g0,kilo*molarmass(U),g0)
```

Examples: `FPS`, `British`, `IPS`, `English`, `Survey`.
