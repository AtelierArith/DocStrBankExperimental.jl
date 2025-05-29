```Julia
earthradius(U::UnitSystem) = sqrt(earthmass(U)*gravitation(U)/gforce(U))
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²g₀⁻¹ᐟ²GME¹ᐟ²τ⋅2 = 1.6509810466(17) × 10¹⁹) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

標準地球二体半径の近似値（単位：mまたはft）。

```

Julia julia> earthradius(KKH) # km g₀⁻¹ᐟ²GME¹ᐟ²2⁻³5⁻³ = 6375.4163237(64) [km] KKH

julia> earthradius(Nautical) # nm τ⁻¹2⁵3³5² = 3437.7467707849396 [nm] Nautical

julia> earthradius(IAU) # au g₀⁻¹ᐟ²au⁻¹GME¹ᐟ² = 4.2617025856(43) × 10⁻⁵ [au] IAU☉ ```
