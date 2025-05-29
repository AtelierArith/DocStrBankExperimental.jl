```
semiminor(P::Planet) = semimajor(P)*(1-flattening(P))
```

Polar radius of oblate `Planet` reference ellipsoid (m).

```Julia
julia> semiminor(Earth) # m
6.356752314245179e6
```
