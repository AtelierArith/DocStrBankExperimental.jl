```
XPRS_QCROOTALG
```

This control determines which algorithm is to be used to solve the root of a mixed integer quadratic constrained or mixed integer second order cone problem, when outer approximation is used. (integer)

Default value: `-1`

Values: -1 : Determined automatically. 0 : Use the barrier algorithm. 1 : Use the dual simplex on a relaxation of the problem constructed using outer approximation.
