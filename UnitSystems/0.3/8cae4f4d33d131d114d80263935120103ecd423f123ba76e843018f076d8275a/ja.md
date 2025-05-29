```Julia
powerdensity(U::UnitSystem,S::UnitSystem) = power(U,S)/volume(U,S)
powerdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/powerdensity(U,S)
```

スペクトル放射照度（体積）または `powerdensity` (W⋅m⁻³)、単位変換係数。

```Julia
julia> powerdensity(CGS,Metric) # kg⋅cm⋅g⁻¹⋅m⁻¹
0.09999999999999995

julia> powerdensity(CGS,English) # lb⋅cm⋅g⁻¹⋅ft⁻¹
0.0020885434233150124

julia> powerdensity(English,Metric) # kg⋅ft⋅lb⁻¹⋅m⁻¹
47.88025898033583
```
