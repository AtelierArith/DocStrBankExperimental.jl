```Julia
frequency(U::UnitSystem,S::UnitSystem) = 1/time(U,S)
frequency(v::Real,U::UnitSystem,S::UnitSystem) = v/frequency(U,S)
```

時間の単位あたりの出現回数（Hzまたはs⁻¹）、単位変換係数。

```Julia
julia> frequency(IAU,Metric) day⋅s⁻¹
1.1574074074074073e-5
```
