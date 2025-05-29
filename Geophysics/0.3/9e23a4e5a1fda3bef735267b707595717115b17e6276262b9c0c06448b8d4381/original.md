```
flattening(P::Planet) = 1-semiminor(P)/semimajor(P)
```

Oblate `flattening` parameter of a `Planet` reference ellipsoid (dimensionless).

```Julia
julia> 1/flattening(Earth)
298.257223563
```
