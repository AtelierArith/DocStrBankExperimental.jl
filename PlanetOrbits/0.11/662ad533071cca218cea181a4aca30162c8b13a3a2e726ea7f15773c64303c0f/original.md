```
radvel(orbit, t)
```

Get the relative radial velocity [m/s] of the  *secondary* vs the *primary* along the line of sight (positive meaning moving away) at the time `t` [days].

```
radvel(o)
```

Get the relative radial velocity [m/s] of the  *secondary* vs the *primary* along the line of sight (positive meaning moving away) from an instance of `AbstractOrbitSolution`.

```
radvel(elem, t, M_planet)
```

Get the absolute radial velocity [m/s] of the  *primary* long the line of sight (positive meaning moving away) at the time `t` [days]. The units of `M_planet` and `elem.M` must match.

```
radvel(o, M_planet)
```

Get the absolute radial velocity [m/s] of the *primary* along the line of sight (positive meaning moving away) from an `AbstractOrbitSolution`. The units of `M_planet` and `elem.M` must match.
