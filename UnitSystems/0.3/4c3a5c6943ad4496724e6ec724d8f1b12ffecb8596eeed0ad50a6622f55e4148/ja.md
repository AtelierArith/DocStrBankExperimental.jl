```Julia
apostilb(U::UnitSystem) = luminance(𝟐/turn(U),U,Metric)
```

`luminance`のメトリック単位 (lx⋅rad⁻²)。

```Julia
julia> apostilb(Engineering) # nt
0.3183098861837907

julia> apostilb(MetricDegree) # lm⋅m⁻²deg⁻²
1.6923189988150477e-6

julia> apostilb(MetricGradian) # lm⋅m⁻²gon⁻²
1.2337005501361699e-6

julia> apostilb(CGS) # sb
3.183098861837908e-5

julia> apostilb(English) # fc
0.029571956088528153
```
