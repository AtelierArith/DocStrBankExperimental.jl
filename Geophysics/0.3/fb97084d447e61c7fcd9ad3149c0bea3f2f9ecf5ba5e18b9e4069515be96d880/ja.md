```
semimajor(P::Planet) = semiminor(P)/(1-flattening(P))
```

扁平な `Planet` 参照楕円体の赤道半径 (m)。

```Julia
julia> semimajor(Earth) # m
6.378137e6
```
