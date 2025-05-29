```
accdec(orbit, t)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of the *secondary* at the time `t` [days].

```
accdec(o)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of the *secondary* from an instance of `AbstractOrbitSolution`.

```
accdec(elem, t, M_planet)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of  the *primary* in at the time `t` [days]. The units of `M_planet` and `elem.M` must match.

```
accdec(o)
```

Get the instantaneous acceleration [mas/julian year^2] in the right-ascension direction of the *primary* from an instance of `AbstractOrbitSolution`. The units of `M_planet` and `elem.M` must match.
