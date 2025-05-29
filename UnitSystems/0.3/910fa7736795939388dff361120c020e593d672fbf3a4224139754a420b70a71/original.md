```
mechanicalheat(U::UnitSystem) = molargas(U)/molargas(Metric)*calorie(Metric)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
```

Heat to raise 1 `mass` unit of water by 1 `temperature` unit, or 1.9859050081929637 `mechanicalheat` per `molaramount` per `temperature` units (J or ft⋅lb).

```Julia
julia> mechanicalheat(Metric) # J
4.186737323211058

julia> mechanicalheat(English) # ft⋅lb
778.1576129990754

julia> mechanicalheat(British) # ft⋅lb
25036.48082518826
```
