```Julia
gram(U::UnitSystem) = mass(𝟏,U,Gauss)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²2⁻⁴5⁻³ = 1.09776910575(34) × 10²⁷) [mₑ] Unified
```

Metric `gram` unit of `mass` (kg or lb).

```Julia
julia> gram(Metric) # kg
2⁻³5⁻³ = 0.001 [kg] Metric

julia> gram(CGS) # g
𝟏 = 1.0 [g] Gauss

julia> gram(English) # lb
lb⁻¹2⁻³5⁻³ = 0.002204622621848776 [lbm] English

julia> gram(British) # slug
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [slug] British

julia> gram(Gravitational) # hyl
g₀⁻¹2⁻³5⁻³ = 0.00010197162129779284 [hyl] Gravitational
```
