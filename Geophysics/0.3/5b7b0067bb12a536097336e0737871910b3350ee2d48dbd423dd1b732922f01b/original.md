```
radius(θ,P::Planet) = 1/sqrt((cos(θ)/semimajor(P,U))^2+(sin(θ)/semiminor(P,U))^2)
```

Parametrized `radius` of `Planet` in terms of geocentric latitude `θ` coordinate (m).
