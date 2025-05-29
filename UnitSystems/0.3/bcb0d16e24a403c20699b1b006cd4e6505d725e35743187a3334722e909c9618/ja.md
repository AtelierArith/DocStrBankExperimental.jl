```Julia
luminousefficacy(U::UnitSystem) = Kcd*power(U)
luminousefficacy(U::UnitSystem{𝟏}) = 𝟏
```

540 THzの単色放射の光束効率 `Kcd` (lm⋅W⁻¹)。

```Julia
julia> luminousefficacy(Metric) # lm⋅W⁻¹
683.01969009009

julia> luminousefficacy(CODATA) # lm⋅W⁻¹
683.019701522891

julia> luminousefficacy(Conventional) # lm⋅W⁻¹
683.0198236454073

julia> luminousefficacy(International) # lm⋅W⁻¹
683.1324069249657

julia> luminousefficacy(British) # lm⋅s³⋅slug⋅ft⁻²
926.0503548878946
```
