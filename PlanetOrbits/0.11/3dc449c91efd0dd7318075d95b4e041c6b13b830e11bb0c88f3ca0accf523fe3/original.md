```
AbstractOrbit
```

Represents a orbit. Contains all the information to calculate the location of a planet at a given time, true anomaly, eccentric anomaly, or mean anomaly. Different concrete implementations of AbstractOrbit contain varying amounts of information.

Basic information about the orbit can be queried using functions like `period(orbit)`.

Orbits can be solved using functions like `orbitsolve(orb)`.

See: `RadialVelocityOrbit`, `KepOrbit`, `VisualOrbit`
