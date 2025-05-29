```
latitudegeodetic(θ,P::Planet) = atan(tan(θ)/(1-flattening(P))^2)
```

Convert geocentric latitude `θ` to geodetic latitude on `Planet` surface (rad).
