```Julia
amagat(U::UnitSystem) = loschmidt(U)/avogadro(U)
```

Number of moles of an ideal gas in a unit volume (mol⋅m⁻³ or lb-mol⋅ft⁻³).

```Julia
julia> amagat(Metric) # mol⋅m⁻³
44.615033390134165

julia> amagat(SI2019) # mol⋅m⁻³
44.615033405470314

julia> amagat(English) # slug-mol⋅ft⁻³
0.002785225545582672
```
