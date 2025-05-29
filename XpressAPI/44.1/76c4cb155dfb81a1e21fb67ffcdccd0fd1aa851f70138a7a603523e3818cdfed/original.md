```
XPRS_BARRHSSCALE
```

Defines how the barrier scales the right hand side. (double)

Default value: `-1`

Values: -1 : Let the optimizer decide. 0 : Scale by geometric mean.

> =0


: Scale such that the largest right hand side coefficient's largest element does not exceed this number.
