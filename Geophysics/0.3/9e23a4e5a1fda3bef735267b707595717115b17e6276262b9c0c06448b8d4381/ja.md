```
flattening(P::Planet) = 1-semiminor(P)/semimajor(P)
```

惑星の基準楕円体の扁平率 `flattening` パラメータ（無次元）。

```Julia
julia> 1/flattening(Earth)
298.257223563
```
