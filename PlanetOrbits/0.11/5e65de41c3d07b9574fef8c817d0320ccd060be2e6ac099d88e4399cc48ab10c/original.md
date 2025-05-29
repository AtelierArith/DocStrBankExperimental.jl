```
accra(orbit, t)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of the *secondary* at the time `t` [days].

```
accra(o)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of the *secondary* from an instance of `AbstractOrbitSolution`.

```
accra(elem, t, M_planet)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of  the *primary* in at the time `t` [days]. The units of `M_planet` and `elem.M` must match.

```
accra(o)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of the *primary* from an instance of `AbstractOrbitSolution`. The units of `M_planet` and `elem.M` must match.
