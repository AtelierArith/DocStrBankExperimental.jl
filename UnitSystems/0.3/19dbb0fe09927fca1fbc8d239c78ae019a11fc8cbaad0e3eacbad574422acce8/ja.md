```Julia
amagat(U::UnitSystem) = loschmidt(U)/avogadro(U)
```

単位体積あたりの理想気体のモル数 (mol⋅m⁻³ または lb-mol⋅ft⁻³)。

```Julia
julia> amagat(Metric) # mol⋅m⁻³
44.615033390134165

julia> amagat(SI2019) # mol⋅m⁻³
44.615033405470314

julia> amagat(English) # slug-mol⋅ft⁻³
0.002785225545582672
```
