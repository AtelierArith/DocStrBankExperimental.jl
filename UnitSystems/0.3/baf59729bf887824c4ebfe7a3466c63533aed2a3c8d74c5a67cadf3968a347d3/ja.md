```Julia
gravityforce(U::UnitSystem,S::UnitSystem) = acceleration(U,S)/specificforce(U,S)
gravityforce(v::Real,U::UnitSystem,S::UnitSystem) = v/gravityforce(U,S)
```

`acceleration` に対する `specificforce` の参照 (𝟏, F⁻¹MLT⁻²)、単位変換係数。

```Julia
julia> gravityforce(Metric,CGS)
1

julia> gravityforce(Metric,Engineering)
9.80665

julia> gravityforce(Metric,English)
32.17404855643044
```
