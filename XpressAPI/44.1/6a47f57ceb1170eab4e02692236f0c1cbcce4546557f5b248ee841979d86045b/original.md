```
XPRS_CROSSOVER
```

Newton barrier and hybrid gradient: This control determines whether the barrier method will cross over to the simplex method when at optimal solution has been found, to provide an end basis (see XPRSgetbasis, XPRSwritebasis) and advanced sensitivity analysis information (see XPRSobjsa, XPRSrhssa, XPRSbndsa). (integer)

Default value: `-1`

Values: -1 : Determined automatically. 0 : No crossover. 1 : Primal crossover first. 2 : Dual crossover first.
