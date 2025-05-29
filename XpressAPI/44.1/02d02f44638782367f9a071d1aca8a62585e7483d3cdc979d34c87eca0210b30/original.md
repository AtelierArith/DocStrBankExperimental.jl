```
XPRS_CROSSOVERACCURACYTOL
```

Newton barrier: This control determines how crossover adjusts the default relative pivot tolerance. (double)

When re-inversion is necessary, crossover will compare the recalculated working basic solution with the assumed ones just before re-inversion took place. If the error is above this threshold, crossover will adjust the relative pivot tolerance to address the build-up of numerical inaccuracies.

Default value: `1e-6`

Domain: ?
