```Julia
poundal(U::UnitSystem) = force(𝟏,U,FPS)
```

Absolute English `poundal` unit of `force` (N or lb).

```Julia
julia> poundal(Metric) # N
0.13825495437600002

julia> poundal(CGS) # dyn
13825.495437600002

julia> poundal(English) # lb
0.031080950171567256

julia> poundal(FPS) # pdl
1

julia> poundal(Engineering) # kp
0.0140980818501731
```
