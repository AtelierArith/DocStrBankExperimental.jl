```
XPRS_BAROBJSCALE
```

Defines how the barrier scales the objective. (double)

Default value: `-1`

Values: -1 : Let the optimizer decide. 0 : Scale by geometric mean.

> =0


: Scale such that the largest objective coefficient's largest element does not exceed this number. In quadratic problems, the quadratic diagonal is used as reference valuses instead of the linear objective.
