```
semimajor(P::Planet) = semiminor(P)/(1-flattening(P))
```

Equatorial radius of oblate `Planet` reference ellipsoid (m).

```Julia
julia> semimajor(Earth) # m
6.378137e6
```
