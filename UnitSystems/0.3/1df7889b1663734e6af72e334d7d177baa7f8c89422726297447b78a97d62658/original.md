```Julia
statutemile(U::UnitSystem) = length(𝟐^5*𝟑*𝟓*𝟏𝟏,U,Survey)
```

Statute `Survey` mile (m or ft).

```Julia
julia> statutemile(Metric) # m
1609.3472186944375

julia> statutemile(English) # ft
5280.01056002112

julia> statutemile(Survey) # ftUS
5280
```
