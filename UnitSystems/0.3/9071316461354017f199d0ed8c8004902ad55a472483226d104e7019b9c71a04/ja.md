```Julia
surveyfoot(U::UnitSystem) = length(𝟏,U,Survey)
```

調査単位の `length` (m または ft)。

```Julia
julia> surveyfoot(Metric) # m
0.3048006096012192

julia> surveyfoot(English) # ft
1.000002000004

julia> surveyfoot(IPS) # in
12.000024000047993
```
