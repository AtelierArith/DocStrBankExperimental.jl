```
XPRS_DUALIZEOPS
```

Bit-vector control for adjusting the behavior when a problem is dualized. (integer)

Default value: `1` (bit `0` is set)

Values are a bitset: bit 0 : Swap the simplex algorithm to run. If dual simplex is selected for the original problem then primal simplex will be run on the dualized problem, and simiarly if primal simplex is selected.
