```
ThieleInnesOrbit(e, tp, M, plx, A, B, F, G)
```

Represents a visual orbit of a planet using Thiele-Innes orbital elements. Convertable to and from a VisualOrbit. This parameterization does not have the issue that traditional angular parameters have where the argument of periapsis and longitude of ascending node become undefined for circular and face on orbits respectively.

!!! warning
    There is a remaining bug in this implementation for pi <= Ω < 2pi

