```Julia
lorentz(U::UnitSystem) = spat(U)*biotsavart(U)/vacuumpermeability(U)/rationalization(U)
nonstandard : [C⁻¹], [𝟙], [𝟙], [𝟙], [𝟙]
C⁻¹ [αL] 統一

ローレンツの法則の力に対する電磁比例定数 `αL`（無次元）。

```

Julia julia> lorentz(Metric) 𝟏 = 1.0 [𝟙] メトリック

julia> lorentz(LorentzHeaviside) 𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] ローレンツ・ヘイヴィサイド

julia> lorentz(Gauss) 𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] ガウス ```
