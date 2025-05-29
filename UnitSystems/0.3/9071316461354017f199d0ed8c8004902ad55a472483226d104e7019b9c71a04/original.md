```Julia
surveyfoot(U::UnitSystem) = length(𝟏,U,Survey)
```

Survey unit of `length` (m or ft).

```Julia
julia> surveyfoot(Metric) # m
0.3048006096012192

julia> surveyfoot(English) # ft
1.000002000004

julia> surveyfoot(IPS) # in
12.000024000047993
```
