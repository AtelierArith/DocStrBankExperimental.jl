```
(U::UnitSystem)(v::Number, d) ↦ Quantity(U,v,d) = Quantity{U}(v,d)
```

Numerical `Quantity` having value `v` with dimension `d` specified in `U::UnitSystem`.

```Julia
julia> Metric(1,energy)
1 [J] Metric

julia> English(1,energy)
1 [lbf⋅ft] English
```

An alternate syntax `Quantity(U::UnitSystem, v::Number, d)` is also available as standard syntax. When `using UnitSystems` instead of `using Similitude`, this same syntax can be written so that code doesn't need to be changed while the output is generated.
