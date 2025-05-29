```
eccentricity2(P::Planet) = eccentricity(P)/sqrt(1-eccentricity(P))
```

扁平な `Planet` 参照楕円体の第二の `eccentricity2`（無次元）。

```Julia
julia> eccentricity2(Earth)
0.08209443794969568
```
