```
orbitsolve(orbit, t, method=Auto())
```

Given an orbit object and a time `t` in days, get the position and velocity of the secondary body (e.g. planet around a star).

This will output a struct that is a subtype of `AbstractOrbitSolution` which we can then query with `raoff`, `decoff`, `radvel`, etc.

You can also calculate those quanitities individually (see their docstrings)  but if you need more than one, it is most efficient to save the orbit solution once.

Note: these calculations use the small angle approximation, so are only accurate when  the star is much further way from the observer than the secondary is from the primary.

See also: `orbitsolve_ν`,  `orbitsolve_meananom`,  `orbitsolve_eccanom`, `projectedseparation`, `raoff`, `decoff`, `radvel`, `propmotionanom`.
