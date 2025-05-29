```
eccentricity(P::Planet) = sqrt(flattening(P)*(2-flattening(P)))
```

扁平な `Planet` 参照楕円体の楕円率 `eccentricity` (無次元)。

```Julia
julia> eccentricity(Earth)
0.08181919084262149
```
