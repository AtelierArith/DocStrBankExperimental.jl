```Julia
kilopond(U::UnitSystem) = force(𝟏,U,Engineering)
```

Gravitational `kilopond` unit of `force` used in engineering systems (N or lb).

```Julia
julia> kilopond(Metric) # N
9.80665

julia> kilopond(CGS) # dyn
980664.9999999998

julia> kilopond(English) # lb
2.2046226218487757

julia> kilopond(FPS) # pdl
70.9316352839675

julia> kilopond(Engineering) # kp
1
```
