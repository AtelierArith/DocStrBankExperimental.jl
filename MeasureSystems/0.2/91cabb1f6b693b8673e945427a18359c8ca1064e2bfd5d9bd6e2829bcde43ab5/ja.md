```Julia
rationalization(U::UnitSystem) = spat(U)*biotsavart(U)/vacuumpermeability(U)/lorentz(U)
demagnetizingfactor : [R], [𝟙], [𝟙], [𝟙], [𝟙]
R [λ] 統一

磁化定数と偏極密度の定義または `spat(U)*coulomb(U)*permittivity(U)`。

```

Julia julia> rationalization(Metric) 𝟏 = 1.0 [𝟙] Metric

julia> rationalization(Gauss) τ⋅2 = 12.566370614359172 [𝟙] Gauss ```
