```
eccentricity2(P::Planet) = eccentricity(P)/sqrt(1-eccentricity(P))
```

Second `eccentricity2` of oblate `Planet reference ellipsoid (dimensionless).

```Julia
julia> eccentricity2(Earth)
0.08209443794969568
```
