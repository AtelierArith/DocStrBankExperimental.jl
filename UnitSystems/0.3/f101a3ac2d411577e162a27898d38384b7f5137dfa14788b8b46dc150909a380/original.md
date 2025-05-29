```Julia
footlambert(U::UnitSystem) = luminance(𝟐/turn(U),U,English)
```

English unit of `luminance` (nt).

```Julia
julia> footlambert(Engineering) # nt
3.426259099635391

julia> footlambert(MetricDegree) # lm⋅m⁻²deg⁻²
1.821597009974106e-5

julia> footlambert(MetricGradian) # lm⋅m⁻²gon⁻²
1.3279442202711239e-5

julia> footlambert(CGS) # sb
0.00034262590996353903

julia> footlambert(English) # fc
0.3183098861837907
```
