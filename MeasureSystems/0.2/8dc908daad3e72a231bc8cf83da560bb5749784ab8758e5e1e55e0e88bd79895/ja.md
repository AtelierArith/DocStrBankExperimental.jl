```Julia
earthgram(U::UnitSystem) = mass(milli,U,Meridian)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⁻³ᐟ²GME³ᐟ²τ³2⁻³¹5⁻²⁴ = 1.1025449025(33) × 10²⁷) [mₑ] 統一

Meridian `gram` 単位の `mass` は `earthmeter` (kg または lb) に基づいています。

```

Julia julia> earthgram(Meridian) # keg 2⁻³5⁻³ = 0.001 [keg] Meridian

julia> earthgram(CGS) # g g₀⁻³ᐟ²GME³ᐟ²τ³2⁻²⁷5⁻²¹ = 1.0043504565(30) [g] ガウス

julia> earthgram(English) # lb g₀⁻³ᐟ²lb⁻¹GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 0.0022142137367(67) [lbm] 英語

julia> earthgram(British) # slug g₀⁻⁵ᐟ²ft⋅lb⁻¹GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 6.881986682(21) × 10⁻⁵ [slug] 英国

julia> earthgram(Gravitational) # hyl g₀⁻⁵ᐟ²GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 0.00010241524440(31) [hyl] 重力 ```
