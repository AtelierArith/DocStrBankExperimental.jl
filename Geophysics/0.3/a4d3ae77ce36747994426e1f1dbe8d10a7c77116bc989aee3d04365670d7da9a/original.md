```
latitudegeocentric(ϕ,P::Planet) = atan(tan(ϕ)*(1-flattening(P))^2)
```

Convert geodetic latitude `ϕ` to geocentric latitude on `Planet` surface (rad).
