```Julia
siderealyear(U::UnitSystem) = gaussianyear(U)/√(𝟏+earthmass(IAU)+lunarmass(IAU))
```

軌道 `time` は `gaussgravitation` 定数 `kG` と地球-月系の `mass` (s) によって定義されます。

```Julia
julia> siderealyear(Metric) # s
3.1558148013226096e7

julia> siderealyear(MPH) # h
8766.152225896136

julia> siderealyear(IAU) # D
365.2563427456724
```
