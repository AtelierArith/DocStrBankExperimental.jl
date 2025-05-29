```Julia
mile(U::UnitSystem) = length(𝟏,U,MPH)
```

法定 `English` マイル (m または ft)。

```Julia
julia> mile(Metric) # m
1609.3440000000003

julia> mile(English) # ft
5280

julia> mile(Nautical) # nm
5279.98944
```
