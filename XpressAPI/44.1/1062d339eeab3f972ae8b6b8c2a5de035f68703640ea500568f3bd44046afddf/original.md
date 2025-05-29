```
XPRS_CUTFACTOR
```

Limit on the number of cuts and cut coefficients the optimizer is allowed to add to the matrix during tree search. (double)

The cuts and cut coefficients are limited by `CUTFACTOR` times the number of rows and coefficients in the initial matrix.

Default value: `-1`

Values: -1 : Let the optimizer decide on the maximum amount of cuts based on CUTSTRATEGY.

> =0


: Multiple of number of rows and coefficients to use.
