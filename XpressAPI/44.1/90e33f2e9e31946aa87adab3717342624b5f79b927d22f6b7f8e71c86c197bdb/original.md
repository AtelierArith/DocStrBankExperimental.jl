```
XPRS_SIFTSWITCH
```

Determines which algorithm to use for solving the subproblems during sifting. (integer)

Default value: `-1`

Values: -1 : Dual simplex. 0 : Barrier.

> 0


: Use the barrier algorithm while the number of dual infeasibilities is larger than this value, otherwise use dual simplex.
