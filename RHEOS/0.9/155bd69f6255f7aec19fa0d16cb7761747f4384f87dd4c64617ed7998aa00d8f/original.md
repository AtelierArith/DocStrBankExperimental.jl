```
exportcsv(self::Union{RheoTimeData, RheoFreqData}, filedir::String; delimiter=',', colorder=nothing)
```

Export `RheoTimeData` or `RheoFreqData` type to csv format. May be useful for plotting/analysis in other software. By default, full time data will be exported with columns ordered as (t, σ, ϵ). Partial time data will be ordered as either (t, σ) or (t, ϵ). Full frequency data will be ordered as (ω, Gp, Gpp). The order of columns can be customised by passing a NamedTuple to the `colorder` arguments. For example (σ = 1, t = 3, ϵ = 2) would export the columns in the order (σ, ϵ, t). As with `importcsv`, the delimiter can be set by keyword argument.
