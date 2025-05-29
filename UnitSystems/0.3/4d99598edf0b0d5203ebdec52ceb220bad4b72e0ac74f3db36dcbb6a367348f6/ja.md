```Julia
candela(U::UnitSystem) = luminousintensity(𝟏,U,Metric)
```

`luminousintensity` (cd) の一般的な単位。

```Julia
julia> candela(Engineering) # lm⋅rad⁻²
1

julia> candela(MetricDegree) # lm⋅deg⁻²
0.00030461741978670857

julia> candela(MetricGradian) # lm⋅gon⁻²
0.00024674011002723397

julia> candela(CGS) # cd
1

julia> candela(English) # cd
1
```
