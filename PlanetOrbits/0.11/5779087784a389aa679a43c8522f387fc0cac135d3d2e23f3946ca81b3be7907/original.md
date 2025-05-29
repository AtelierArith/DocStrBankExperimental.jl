```
posangle(orbit, t)
```

Calculate the position angle [rad] of the secondary about its primary from our perspective at the time `t` [days].

```
posangle(o)
```

Calculate the position angle [rad] of the secondary about its primary from our perspective from an instance of `AbstractOrbitSolution`.

```
posangle(elem, t, M_planet)
```

Calculate the position angle [rad] of the secondary about its primary from our perspective at the time `t` [days]. In this case only, the value of M_planet can be arbitrary.

```
posangle(o, M_planet)
```

Calculate the position angle [rad] of the **primary**  from our perspective from an instance of `AbstractOrbitSolution`. In this case only, the value of M_planet can be arbitrary.
