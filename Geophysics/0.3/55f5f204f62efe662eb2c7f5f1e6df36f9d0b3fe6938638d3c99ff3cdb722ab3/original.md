```
eccentricity(P::Planet) = sqrt(flattening(P)*(2-flattening(P)))
```

Elliptic `eccentricity` of oblate `Planet` reference ellipsoid (dimensionless).

```Julia
julia> eccentricity(Earth)
0.08181919084262149
```
