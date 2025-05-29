```Julia
IAUE = EntropySystem(Metric,DAY,LD,GME/G)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

Astronomical (Earth) `UnitSystem` defined by `lunardistance` around the `earthmass`.

```Julia
julia> boltzmann(IAUE) # ME⋅LD²⋅D⁻²⋅K⁻¹
kB⋅NA⋅𝘩²R∞⋅α⁻²μₑᵤ⁻¹mP⁻²GME⁻¹τ⁻¹2¹²5/202692169 = 1.167923(26) × 10⁻⁵⁵ [ME⋅LD²D⁻²K⁻¹] IAUE

julia> planckreduced(IAUE) # ME⋅LD²⋅D⁻¹⋅rad⁻¹
𝘩²𝘤⋅mP⁻²GME⁻¹τ⁻²2⋅3⁻³5⁻⁴/202692169 = 1.032508(23) × 10⁻⁷¹ [ME⋅LD²D⁻¹] IAUE

julia> lightspeed(IAUE) # LD⋅D⁻¹
𝘤⋅2⁴5⁻¹/14237 = 67383.2876027253 [LD⋅D⁻¹] IAUE

julia> vacuumpermeability(IAUE) # ME⋅LD²⋅C⁻²
𝘩⋅𝘤⋅mP⁻²GME⁻¹2⁻⁹3⁻³5⁻¹⁰/14237 = 5.47389(12) × 10⁻⁴⁰ [ME⋅LD⋅C⁻²] IAUE

julia> electronmass(IAUE) # ME
𝘩²R∞⋅α⁻²mP⁻²GME⁻¹τ⁻¹2 = 1.525306(34) × 10⁻⁵⁵ [ME] IAUE

julia> molarmass(IAUE) # ME⋅mol⁻¹
𝘩⋅𝘤⋅mP⁻²GME⁻¹τ⁻¹2⁻³5⁻³ = 1.674434(37) × 10⁻²⁸ [ME⋅mol⁻¹] IAUE

julia> luminousefficacy(IAUE) # lm⋅D³⋅ME⁻¹⋅LD⁻²
𝘩⁻¹𝘤⁻¹Kcd⋅mP²GME⋅τ⋅2⁻¹⁵3⁻³⋅202692169 = 9.34520(21) × 10²⁹ [ME⁻¹LD⁻²D³lm] IAUE

julia> turn(IAU)/gaussianmonth(IAU) # D⁻¹
GME¹ᐟ²2⁵ᐟ²3⁻³ᐟ²5⁻⁵ᐟ²/1.6987431854323947×10⁶ = 0.22888074402(23) [D⁻¹] IAU☉
```
