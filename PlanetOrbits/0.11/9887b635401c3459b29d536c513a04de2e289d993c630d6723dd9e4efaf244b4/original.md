```
pmdec(orbit, t)
```

Get the instantaneous proper motion anomaly [mas/julian year] in declination of the *secondary* at the time `t` [days].

```
pmdec(o)
```

Get the instantaneous proper motion anomaly [mas/julian year] in declination of the *secondary* from an instance of `AbstractOrbitSolution`.

```
pmdec(elem, t, M_planet)
```

Get the instantaneous proper motion anomaly [mas/julian year] in declination of  the *primary* in at the time `t` [days]. The units of `M_planet` and `elem.M` must match.

```
pmdec(o, M_planet)
```

Same as above, but from an orbit solution.
