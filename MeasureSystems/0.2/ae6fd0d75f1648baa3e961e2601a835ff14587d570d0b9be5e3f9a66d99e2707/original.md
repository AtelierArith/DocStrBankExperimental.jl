```Julia
cosmological(U::UnitSystem) = 𝟑*darkenergydensity(U)*(hubble(U)/lightspeed(U))^2
fuelefficiency : [L⁻²], [L⁻²], [L⁻²], [L⁻²], [L⁻²]
L⁻²⋅(𝘤⁻²R∞⁻²α⁴ΩΛ⋅H0²au⁻²2⁻²²3⁻⁷5⁻¹² = 1.649(24) × 10⁻⁷⁷) [ħ⁻²𝘤²mₑ²ϕ⁻²g₀⁻²] Unified
```

Cosmological constant from Einstein's controversial theory expanded on by Hubble.

```Julia
julia> cosmological(Metric)
𝘤⁻²ΩΛ⋅H0²au⁻²τ²2⁻²⁰3⁻⁷5⁻¹² = 1.106(16) × 10⁻⁵² [m⁻²] Metric

julia> cosmological(Hubble)
ΩΛ⋅3 = 2.067(17) [T⁻²] Hubble

julia> cosmological(Cosmological)
τ⋅2² = 25.132741228718345 [T⁻²] Cosmological
```
