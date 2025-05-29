```Julia
poundforce(U::UnitSystem) = force(𝟏,U,English)
```

英語の `poundforce` 単位は、工学システムで使用される `force` (N または lb) です。

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
