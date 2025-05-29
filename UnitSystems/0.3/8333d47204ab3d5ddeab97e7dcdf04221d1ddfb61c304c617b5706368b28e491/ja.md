```Julia
susceptibility(U::UnitSystem,S::UnitSystem) = 1/rationalization(U,S)
susceptibility(v::Real,U::UnitSystem,S::UnitSystem) = v/susceptibility(U,S)
```

磁気/電気体積 `susceptibility`（無次元）、単位変換係数。

```Julia
julia> susceptibility(EMU,Metric)
12.566370614359172

julia> susceptibility(ESU,Metric)
12.566370614359172

julia> susceptibility(Metric,SI2019)
1
```
