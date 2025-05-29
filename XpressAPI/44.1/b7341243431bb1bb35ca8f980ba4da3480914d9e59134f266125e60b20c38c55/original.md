```
XPRS_BARSTART
```

Controls the computation of the starting point and warm-starting for the Newton barrier and the hybrid gradient algorithms. (integer)

Default value: 0

Values: -1 : Uses the existing solution for warm-start if one is available. 0 : Warm-start is disabled; the starting point is determined automatically from the next three options. 1 : Uses simple heuristics to compute the starting point based on the magnitudes of the matrix entries. 2 : Uses the pseudoinverse of the constraint matrix to determine primal and dual initial solutions. Less sensitive to scaling and numerically more robust, but in several case less efficient than 1. 3 : Uses the unit starting point for the homogeneous self-dual barrier algorithm.
