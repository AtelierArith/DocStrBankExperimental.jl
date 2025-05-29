```Julia
greatcircle(U::UnitSystem) = τ*earthradius(U)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²g₀⁻¹ᐟ²GME¹ᐟ²τ²2 = 1.0373419854(11) × 10²⁰) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] Unified
```

Approximate `length` of standard Earth two-body circle consistent with units (m or ft).

```Julia
julia> greatcircle(KKH) # km
g₀⁻¹ᐟ²GME¹ᐟ²τ⋅2⁻³5⁻³ = 40057.922172(40) [km] KKH

julia> greatcircle(Nautical) # nm
2⁵3³5² = 21600.0 [nm] Nautical

julia> greatcircle(IAU) # au
g₀⁻¹ᐟ²au⁻¹GME¹ᐟ²τ = 0.00026777067070(27) [au] IAU☉
```
