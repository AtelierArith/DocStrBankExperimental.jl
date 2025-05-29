```Julia
footcandle(U::UnitSystem) = illuminance(𝟏,U,English)
illuminance : [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²J⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸ft⁻²τ⁻³2⁻⁴ = 3.6973037742(45) × 10⁻³⁵) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻³g₀⁻⁴] 統一

英語単位の `illuminance` (lx)。

```

Julia julia> footcandle(Metric) # lx ft⁻² = 10.76391041670972 [lx] メトリック

julia> footcandle(CGS) # ph ft⁻²2⁻⁴5⁻⁴ = 0.0010763910416709721 [ph] ガウス

julia> footcandle(English) # fc 𝟏 = 1.0 [fc] 英語 ```
