```Julia
second(U::UnitSystem) = time(𝟏,U,Metric)
```

Unit of `time` defined by `hyperfine` transition frequency of Cs-133 atom (s).

```Julia
julia> second(Metric) # s
1

julia> second(MPH) # h
0.0002777777777777777

julia> second(IAU) # D
1.1574074074074073e-5
```
