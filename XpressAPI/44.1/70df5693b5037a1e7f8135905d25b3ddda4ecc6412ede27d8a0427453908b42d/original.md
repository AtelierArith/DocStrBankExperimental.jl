```
XPRS_PRECOEFELIM
```

Presolve: Specifies whether the optimizer should attempt to recombine constraints in order to reduce the number of non zero coefficients when presolving a mixed integer problem. (integer)

Default value: `2`

Values: 0 : Disabled. 1 : Remove as many coefficients as possible. 2 : Cautious eliminations. Will not perform a reduction if it might destroy problem structure useful to e.g. heuristics or cutting.
