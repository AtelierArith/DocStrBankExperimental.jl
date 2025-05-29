```Julia
earthgram(U::UnitSystem) = mass(milli,U,Meridian)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⁻³ᐟ²GME³ᐟ²τ³2⁻³¹5⁻²⁴ = 1.1025449025(33) × 10²⁷) [mₑ] Unified
```

Meridian `gram` unit of `mass` based on `earthmeter` (kg or lb).

```Julia
julia> earthgram(Meridian) # keg
2⁻³5⁻³ = 0.001 [keg] Meridian

julia> earthgram(CGS) # g
g₀⁻³ᐟ²GME³ᐟ²τ³2⁻²⁷5⁻²¹ = 1.0043504565(30) [g] Gauss

julia> earthgram(English) # lb
g₀⁻³ᐟ²lb⁻¹GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 0.0022142137367(67) [lbm] English

julia> earthgram(British) # slug
g₀⁻⁵ᐟ²ft⋅lb⁻¹GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 6.881986682(21) × 10⁻⁵ [slug] British

julia> earthgram(Gravitational) # hyl
g₀⁻⁵ᐟ²GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 0.00010241524440(31) [hyl] Gravitational
```
