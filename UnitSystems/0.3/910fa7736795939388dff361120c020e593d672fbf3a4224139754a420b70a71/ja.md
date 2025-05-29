```
mechanicalheat(U::UnitSystem) = molargas(U)/molargas(Metric)*calorie(Metric)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
```

1 `質量` 単位の水を 1 `温度` 単位だけ上昇させるための熱、または 1.9859050081929637 `mechanicalheat` を `モル量` あたり `温度` 単位 (J または ft⋅lb) です。

```Julia
julia> mechanicalheat(Metric) # J
4.186737323211058

julia> mechanicalheat(English) # ft⋅lb
778.1576129990754

julia> mechanicalheat(British) # ft⋅lb
25036.48082518826
```
