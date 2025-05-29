```Julia
demagnetizingfactor : [R], [𝟙], [𝟙], [𝟙], [𝟙]
demagnetizingfactor(U::UnitSystem,S::UnitSystem) = 1/susceptibility(U,S)
demagnetizingfactor(v::Real,U::UnitSystem,S::UnitSystem) = v/demagnetizingfactor(U,S)
R [λ] 統一

`demagnetizingfactor`の量（無次元）、単位変換係数。

```

Julia julia> demagnetizingfactor(EMU,Metric) τ⁻¹2⁻¹ = 0.07957747154594767 [𝟙]/[𝟙] EMU -> Metric

julia> demagnetizingfactor(ESU,Metric) τ⁻¹2⁻¹ = 0.07957747154594767 [𝟙]/[𝟙] ESU -> Metric

julia> demagnetizingfactor(Metric,SI2019) 𝟏 = 1.0 [𝟙]/[𝟙] Metric -> SI2019 ```
