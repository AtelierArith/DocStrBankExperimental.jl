```Julia
Cosmological = AstronomicalSystem(Metric,lc/𝘤,lc,mc)
F=MT⁻¹, M, L=T, T, Q, Θ=M, N=M, J, A=𝟙, R=𝟙, C=𝟙
```

Cosmological scale `UnitSystem` defined by `darkenergydensity`.

```Julia
julia> boltzmann(Cosmological)
𝟏 = 1.0 [𝟙] Cosmological

julia> planckreduced(Cosmological)
𝘩²𝘤⁻⁴ΩΛ⋅H0²au⁻²mP⁻²2⁻²⁰3⁻⁷5⁻¹² = 2.888(43) × 10⁻¹²² [MT] Cosmological

julia> lightspeed(Cosmological)
𝟏 = 1.0 [𝟙] Cosmological

julia> vacuumpermeability(Cosmological)
τ⋅2 = 12.566370614359172 [MTQ⁻²] Cosmological

julia> electronmass(Cosmological)
𝘩²𝘤⁻³R∞⋅α⁻²ΩΛ¹ᐟ²H0⋅au⁻¹mP⁻²τ¹ᐟ²2⁻⁸3⁻⁷ᐟ²5⁻⁶ = 3.566(26) × 10⁻⁸³ [M] Cosmological

julia> molarmass(Cosmological)
𝟏 = 1.0 [𝟙] Cosmological

julia> luminousefficacy(Cosmological)
𝟏 = 1.0 [M⁻¹TJ] Cosmological

julia> hubble(Cosmological)
ΩΛ⁻¹ᐟ²τ¹ᐟ²2⋅3⁻¹ᐟ² = 3.487(14) [T⁻¹] Cosmological

julia> cosmological(Cosmological)
τ⋅2² = 25.132741228718345 [T⁻²] Cosmological
```
