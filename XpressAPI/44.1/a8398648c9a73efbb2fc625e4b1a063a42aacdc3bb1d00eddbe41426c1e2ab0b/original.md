```
XPRS_CHOLESKYTOL
```

Newton barrier: The tolerance for pivot elements in the Cholesky decomposition of the normal equations coefficient matrix, computed at each iteration of the barrier algorithm. (double)

If the absolute value of the pivot element is less than or equal to `CHOLESKYTOL`, it merits special treatment in the Cholesky decomposition process.

Default value: `1.0E-15`

Domain: [-INF,+INF]
