```Julia
spectralexposure(U::UnitSystem,S::UnitSystem) = force(U,S)/speed(U,S)
spectralexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/spectralexposure(U,S)
```

Spectral exposure or `fluence` per `frequency` (N⋅s⋅m⁻¹, J⋅s⋅m⁻²), unit conversion factor.

```Julia
julia> spectralexposure(CGS,Metric) # kg⋅g⁻¹
0.001

julia> spectralexposure(CGS,English) # lb⋅g⁻¹
6.852176585679175e-5

julia> spectralexposure(CODATA,Metric) # kg⋅kg⁻¹
1.000000016738611

julia> spectralexposure(Conventional,Metric) # kg⋅kg⁻¹
1.000000195536555

julia> spectralexposure(English,Metric) # kg⋅lb⁻¹
14.593902937206362
```
