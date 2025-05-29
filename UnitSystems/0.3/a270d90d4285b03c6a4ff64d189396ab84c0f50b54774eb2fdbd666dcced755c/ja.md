```Julia
second(U::UnitSystem) = time(𝟏,U,Metric)
```

単位 `time` は Cs-133 原子のハイパーファイン遷移周波数によって定義されます (s)。

```Julia
julia> second(Metric) # s
1

julia> second(MPH) # h
0.0002777777777777777

julia> second(IAU) # D
1.1574074074074073e-5
```
