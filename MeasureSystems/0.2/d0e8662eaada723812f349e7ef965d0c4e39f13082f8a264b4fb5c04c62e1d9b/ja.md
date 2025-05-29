```Julia
earthmole(U::UnitSystem) = molaramount(𝟏,U,Meridian)
molaramount : [N], [N], [N], [N], [N]
N⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⁻³ᐟ²GME³ᐟ²τ³2⁻³¹5⁻²⁴ = 1.1025449025(33) × 10²⁷) [mₑ⋅Mᵤ⁻¹] 統一

分子 `molaramount` 単位 (mol または lb-mol)。

```

Julia julia> earthmole(Metric) # mol g₀⁻³ᐟ²GME³ᐟ²τ³2⁻²⁷5⁻²¹ = 1.0043504565(30) [mol] メトリック

julia> earthmole(English) # lb-mol g₀⁻³ᐟ²lb⁻¹GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 0.0022142137367(67) [lb-mol] 英語

julia> earthmole(British) # slug-mol g₀⁻⁵ᐟ²ft⋅lb⁻¹GME³ᐟ²τ³2⁻³⁰5⁻²⁴ = 6.881986682(21) × 10⁻⁵ [slug-mol] ブリティッシュ ```
