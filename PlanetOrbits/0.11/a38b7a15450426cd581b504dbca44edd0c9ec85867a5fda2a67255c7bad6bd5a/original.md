```
eccanom(orbit, t)
```

Get the eccentric anomaly [radians] of the *secondary* at the time `t` [days].

```
eccanom(o)
```

Get the eccentric anomaly [radians] of the *secondary* from an instance of `AbstractOrbitSolution`.

Note that for hyperbolic orbits, eccentric anomaly is not defined and the hyperbolic anomaly is returned instead.
