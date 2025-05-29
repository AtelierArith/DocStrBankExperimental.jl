```Julia
eotvos(U::UnitSystem) = specificforce(nano,U,Gauss)/length(𝟏,U,Gauss)
```

重力測定に使用される `specificforce` のメートル法単位（s⁻² または gal⋅cm⁻¹）。

```Julia
julia> eotvos(Metric) # s⁻²
9.999999999999999e-10

julia> eotvos(CGS) # gal⋅cm⁻¹
1.0e-9

julia> eotvos(English) # lbf⋅lbm⁻¹ft⁻¹
3.108095017156726e-11
```
