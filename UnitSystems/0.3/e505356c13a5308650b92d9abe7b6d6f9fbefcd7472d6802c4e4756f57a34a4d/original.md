```Julia
nit(U::UnitSystem) = luminance(𝟏,U,Metric)
```

Metric unit of `luminance` (lx⋅rad⁻²).

```Julia
julia> nit(Engineering) # nt
1

julia> nit(MetricDegree) # lm⋅m⁻²deg⁻²
0.00030461741978670857

julia> nit(MetricGradian) # lm⋅m⁻²gon⁻²
0.00024674011002723397

julia> nit(CGS) # sb
0.00010000000000000003

julia> nit(English) # fc
0.09290304
```
