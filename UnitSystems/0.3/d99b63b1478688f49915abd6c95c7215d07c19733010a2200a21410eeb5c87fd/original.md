```
ElectricSystem(U::UnitSystem,Ω,V) = EntropySystem(U,𝟏,𝟏,V^2/Ω,𝟏,vacuumpermeability(U)/Ω)
```

Constructs new `UnitSystem` from `U` with `mass` rescaled by `electricpotential` and `resistance`. In the `International` system, `Ωᵢₜ` and `Vᵢₜ` are used as definitions from the more recent United States results, while in `InternationalMean` an earlier estimate based on other nations was used.
