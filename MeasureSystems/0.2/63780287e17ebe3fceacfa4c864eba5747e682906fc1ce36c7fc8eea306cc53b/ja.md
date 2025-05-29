```Julia
gaussianyear(U::UnitSystem) = turn(U)/gaussgravitation(U)
time : [T], [T], [T], [T], [T]
T⋅(𝘤⋅R∞⋅α⁻²kG⁻¹τ⋅2¹⁵3⁷5⁵ = 2.45000183355(75) × 10²⁸) [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] 統一

Orbit `time` は、無視できる `mass` の衛星 (s) のための `gaussgravitation` 定数 `kG` によって定義されます。

```

Julia julia> gaussianyear(Metric) # s kG⁻¹2¹⁴3⁷5⁵ = 3.155819598840209×10⁷ [s] メトリック

julia> gaussianyear(MPH) # h kG⁻¹2¹⁰3⁵5³ = 8766.165552333914 [h] MPH

julia> gaussianyear(IAU) # D kG⁻¹2⁷3⁴5³ = 365.2568980139131 [D] IAU☉ ```
