```Julia
siderealyear(U::UnitSystem) = gaussianyear(U)/√(𝟏+earthmass(IAU)+lunarmass(IAU))
```

Orbit `time` defined by `gaussgravitation` constant `kG` and Earth-Moon system `mass` (s).

```Julia
julia> siderealyear(Metric) # s
3.1558148013226096e7

julia> siderealyear(MPH) # h
8766.152225896136

julia> siderealyear(IAU) # D
365.2563427456724
```
