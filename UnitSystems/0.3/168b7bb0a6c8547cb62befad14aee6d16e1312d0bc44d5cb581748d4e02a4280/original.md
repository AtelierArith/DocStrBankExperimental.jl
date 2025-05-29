```
GaussSystem(U::UnitSystem,μ0,λ,αL=𝟏,l=centi,m=milli,g0=gravity(U))
```

Constructs new `UnitSystem` from `U` rescaled for `CGS` with electromagnetic options. The first three options are to set the values for `vacuumpermeability`, `rationalization`, and `lorentz` constants. The following two parameters are scaling for `length` and `mass`, while the last is an option to change the `gravity` reference.

Examples include `EMU`, `ESU`, `Gauss`, `LorentzHeaviside`, and `Kennelly`.
