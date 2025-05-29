```Julia
poundforce(U::UnitSystem) = force(𝟏,U,English)
```

English `poundforce` unit of `force` used in engineering systems (N or lb).

```Julia
julia> poundforce(Metric) # N
4.4482216152605005

julia> poundforce(CGS) # dyn
444822.16152605

julia> poundforce(English) # lb
1

julia> poundforce(FPS) # pdl
32.17404855643044

julia> poundforce(Engineering) # kp
0.45359237
```
