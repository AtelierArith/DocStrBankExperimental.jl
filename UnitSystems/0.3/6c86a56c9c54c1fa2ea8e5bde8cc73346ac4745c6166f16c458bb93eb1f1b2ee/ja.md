```Julia
kilopond(U::UnitSystem) = force(𝟏,U,Engineering)
```

工学システムで使用される重力の `kilopond` 単位 (N または lb)。

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
