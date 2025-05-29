```Julia
footlambert(U::UnitSystem) = luminance(𝟐/turn(U),U,English)
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸ft⁻²τ⁻⁴2⁻³ = 1.1768883436(14) × 10⁻³⁵) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] 統一

English unit of `luminance` (nt).

```

Julia julia> footlambert(Engineering) # nt ft⁻²τ⁻¹2 = 3.42625909963539 [nt] 工学

julia> footlambert(MetricDegree) # lm⋅m⁻²deg⁻² ft⁻²τ⋅2⁻⁵3⁻⁴5⁻² = 0.001043698206451664 [m⁻²lm⋅deg⁻²] メトリック度

julia> footlambert(MetricGradian) # lm⋅m⁻²gon⁻² ft⁻²τ⋅2⁻⁷5⁻⁴ = 0.0008453955472258477 [m⁻²lm⋅gon⁻²] メトリックグラディアン

julia> footlambert(CGS) # sb ft⁻²τ⁻¹2⁻³5⁻⁴ = 0.00034262590996353903 [ph] ガウス

julia> footlambert(English) # fc τ⁻¹2 = 0.3183098861837907 [ft⁻²lm⋅rad⁻²] 英語 ```
