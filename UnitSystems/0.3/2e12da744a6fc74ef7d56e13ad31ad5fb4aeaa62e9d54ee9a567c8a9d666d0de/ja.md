```Julia
bril(U::UnitSystem) = centi*nano*lambert(U)
```

輝度の基準単位 (nt)。

```Julia
julia> bril(Engineering) # nt
3.183098861837906e-8

julia> bril(MetricDegree) # lm⋅m⁻²deg⁻²
1.692318998815047e-13

julia> bril(MetricGradian) # lm⋅m⁻²gon⁻²
1.23370055013617e-13

julia> bril(CGS) # sb
3.183098861837907e-12

julia> bril(English) # fc
2.9571956088528152e-9
```
