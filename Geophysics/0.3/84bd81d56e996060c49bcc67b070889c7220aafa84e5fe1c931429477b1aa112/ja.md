```
secondzonhalharmonic(P::Planet) = -dynamicformfactor(P)/sqrt(5)
```

天体の `secondzonalharmonic` の球面近似（無次元）。

```Julia
julia> secondzonalharmonic(Earth)
-0.000484166754312094
```
