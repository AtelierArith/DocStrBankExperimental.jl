```
latitudeparametric(ϕ,P::Planet) = atan(tan(ϕ)*(1-flattening(P)))
```

Convert geodetic latitude `ϕ` to parametric latitude on surrounding sphere (rad).
