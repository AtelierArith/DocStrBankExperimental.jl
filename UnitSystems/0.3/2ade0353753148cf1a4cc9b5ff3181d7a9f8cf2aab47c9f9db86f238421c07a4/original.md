```
EntropySystem(U::UnitSystem,t,l,m,θ=𝟏)
EntropySystem(U::UnitSystem,t,l,m,θ,μ0,Mu=molarmass(U)/m,g0=gravity(U))
```

Constructs new `UnitSystem` from `U` rescaled along `time`, `length`, `mass`, and `temperature` by the first four parameters. Additional optional parameters allow for customization of the `vacuumpermeability`, `molarmass`, and `gravity` constants.

Examples of this type include `Nautical`, `Meridian`, `Gravitational`, `MTS`, `KKH`, `MPH`, `IAU☉`, `IAUE`, `IAUJ`, `Hubble`, `Cosmological`, `CosmologicalQuantum`. However, most other constructors for `UnitSystem` derivations are based on internally calling `EntropySystem`, such as `AstronomicalSystem`, `ElectricSystem`, `GaussSystem`, and `RankineSystem`. This means `EntropySystem` also constructs the examples listed there.
