```Julia
gaussianyear(U::UnitSystem) = turn(U)/gaussgravitation(U)
```

Orbit `time` defined by `gaussgravitation` constant `kG` for neglible `mass` satellite (s).

```Julia
julia> gaussianyear(Metric) # s
3.1558195988402087e7

julia> gaussianyear(MPH) # h
8766.16555233391

julia> gaussianyear(IAU) # D
365.25689801391303
```
