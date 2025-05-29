```
semiminor(P::Planet) = semimajor(P)*(1-flattening(P))
```

扁平な `Planet` 参照楕円体の極半径 (m)。

```Julia
julia> semiminor(Earth) # m
6.356752314245179e6
```
