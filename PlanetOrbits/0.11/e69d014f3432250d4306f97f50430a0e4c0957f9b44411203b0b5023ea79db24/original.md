```
pmra(orbit, t)
```

Get the instantaneous proper motion anomaly [mas/julian year] in right-ascension of the *secondary* at the time `t` [days].

```
pmra(o)
```

Get the instantaneous proper motion anomaly [mas/julian year] in right-ascension of the *secondary* from an instance of `AbstractOrbitSolution`.

```
pmra(elem, t, M_planet)
```

Get the instantaneous proper motion anomaly [mas/julian year] in right-ascension of  the *primary* in at the time `t` [days]. The units of `M_planet` and `elem.M` must match.

```
pmra(o, M_planet)
```

Same as above, but from an orbit solution.
