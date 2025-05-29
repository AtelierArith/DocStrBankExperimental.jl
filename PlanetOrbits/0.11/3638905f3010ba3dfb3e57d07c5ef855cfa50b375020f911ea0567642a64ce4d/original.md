```
orbit(...)
```

Construct an orbit from the provided keyword arguments. Will automatically select a subclass of AbstractOrbit based on the information provided. This is a convenience function that is not type stable and should not be used in performance sensitive contexts. Instead, call one of the concrete constructors `KepOrbit`, `VisualOrbit`, or `RadialVelocityOrbit` directly. This function logs the kind of elements created so that it's easy to select the correct constructor.

Required arguments:

  * a: semi-major axis [AU]
  * M: gravitational parameter [M⊙]

Optional arguments:

  * tp: epoch of periastron passage, default=0
  * e: eccentricity, default=0
  * ω: argument of periapsis [rad], default=0
  * i: inclination [rad]
  * Ω: longitude of ascending node [rad]
  * plx: parallax [mas]; defines the distance to the primary
