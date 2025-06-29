```
MetricSystem(Mu=Mᵤ,μ0=μ₀,Ru=Rᵤ,g0=𝟏,θ=𝟏,h=𝘩,me=R∞*𝟐*h/𝘤/α^2)
```

Constructs new `UnitSystem` from `molarmass` constant, `vacuumpermeability`, `molargas` constant, `gravity` force reference, `angle` scale, and `planck` constant.

```Julia
UnitSystem(Ru*me/Mu/μₑᵤ/g0,h/τ/g0/θ,𝘤,μ0,me,Mu,Kcd*(mₑ/me)^2*(h/𝘩)*g0,θ,𝟏,𝟏,g0)
```

Examples include `SI2019`, `SI1976`, `Metric`, `Engineering`, `MetricTurn`, `MetricSpatian`, `MetricGradian`, `MetricDegree`, `MetricArcminute`, `MetricArcsecond`. In addition, the `ConventionalSystem` constructor further builds on `MetricSystem`, resulting in variations.

Other derived `UnitSystem` instances such as `British` or `English` or `IAU` are derived from an existing `Metric` specification generated by `MetricSystem`. The constructor `MetricSystem` incorporates several standard common numerical values and exposes variable arguments which can be substituted for customization, yielding the capability to generate historical variations having a common `Universe`. Derivative constructors are `EntropySystem`, `ElectricSystem`, `GaussSystem`, `RankineSystem`, and `AstronomicalSystem`.
