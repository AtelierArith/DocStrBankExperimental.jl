```
AbstractOrbitSolution
```

Represents the solution of an orbit. Contains all the information of an AbstractOrbit, plus information necessary to uniquely locate a planet.

The solution can be queried using a variety of functions such as `radvel(solution)`.

The API for creating orbit solutions it not considered public as the fields may change between minor versions. Instead, create solutions only through the public `orbitsolve` and `orbitsolve_...` functions.
