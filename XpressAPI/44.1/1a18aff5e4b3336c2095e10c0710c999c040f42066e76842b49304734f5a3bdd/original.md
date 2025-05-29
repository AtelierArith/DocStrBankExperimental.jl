```
XPRS_SCALING
```

This bit vector control determines how the Optimizer will rescale a model internally before optimization. (integer)

If set to `0`, no scaling will take place.

Default value: `163`, meaning bits 0, 1, 5 and 7 are set

Values are a bitset: bit 0 : Row scaling. bit 1 : Column scaling. bit 2 : Row scaling again. bit 3 : Maximum. bit 4 : Curtis-Reid. bit 5 : 0: scale by geometric mean.1: scale by maximum element. bit 6 : Treat big-M rows as normal rows. bit 7 : Scale objective function for the simplex method. bit 8 : Exclude the quadratic part of constraint when calculating scaling factors. bit 9 : Scale before presolve. bit 10 : Do not scale rows up. bit 11 : Do not scale columns down. bit 12 : Do not apply automatic objective scaling. bit 13 : RHS scaling. bit 14 : Disable aggressive quadratic scaling. bit 15 : Enable explicit linear slack scaling.
