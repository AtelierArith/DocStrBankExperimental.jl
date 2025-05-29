```Julia
susceptibility : [R⁻¹], [𝟙], [𝟙], [𝟙], [𝟙]
susceptibility(U::UnitSystem,S::UnitSystem) = 1/rationalization(U,S)
susceptibility(v::Real,U::UnitSystem,S::UnitSystem) = v/susceptibility(U,S)
R⁻¹ [λ⁻¹] Unified
```

Magnetic/electric volume `susceptibility` (dimensionless), unit conversion factor.

```Julia
julia> susceptibility(EMU,Metric)
τ⋅2 = 12.566370614359172 [𝟙]/[𝟙] EMU -> Metric

julia> susceptibility(ESU,Metric)
τ⋅2 = 12.566370614359172 [𝟙]/[𝟙] ESU -> Metric

julia> susceptibility(Metric,SI2019)
𝟏 = 1.0 [𝟙]/[𝟙] Metric -> SI2019
```
