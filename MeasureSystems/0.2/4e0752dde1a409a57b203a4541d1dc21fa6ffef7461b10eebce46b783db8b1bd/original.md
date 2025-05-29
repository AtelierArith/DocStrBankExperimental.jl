```Julia
lorentz(U::UnitSystem) = spat(U)*biotsavart(U)/vacuumpermeability(U)/rationalization(U)
nonstandard : [C⁻¹], [𝟙], [𝟙], [𝟙], [𝟙]
C⁻¹ [αL] Unified
```

Electromagnetic proportionality constant `αL` for the Lorentz's law force (dimensionless).

```Julia
julia> lorentz(Metric)
𝟏 = 1.0 [𝟙] Metric

julia> lorentz(LorentzHeaviside)
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] LorentzHeaviside

julia> lorentz(Gauss)
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] Gauss
```
