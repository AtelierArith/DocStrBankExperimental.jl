```Julia
lightspeed(U::UnitSystem) = 𝟏/sqrt(vacuumpermeability(U)*vacuumpermittivity(U))/lorentz(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹ [𝘤] 統一

真空中の光速 `𝘤` は、質量のない粒子のための (m⋅s⁻¹ または ft⋅s⁻¹)。

```

Julia julia> lightspeed(Metric) # m⋅s⁻¹ 𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] メトリック

julia> lightspeed(English) # ft⋅s⁻¹ 𝘤⋅ft⁻¹ = 9.835710564304461×10⁸ [ft⋅s⁻¹] 英語

julia> lightspeed(IAU) # au⋅D⁻¹ 𝘤⋅au⁻¹2⁷3³5² = 173.1446326742(35) [au⋅D⁻¹] IAU☉ ```
