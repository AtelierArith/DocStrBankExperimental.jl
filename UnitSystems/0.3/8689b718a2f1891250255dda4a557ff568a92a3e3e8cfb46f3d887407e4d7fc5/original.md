```Julia
mile(U::UnitSystem) = length(𝟏,U,MPH)
```

Statute `English` mile (m or ft).

```Julia
julia> mile(Metric) # m
1609.3440000000003

julia> mile(English) # ft
5280

julia> mile(Nautical) # nm
5279.98944
```
