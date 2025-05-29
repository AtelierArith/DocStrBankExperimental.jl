```
XPRS_BARITERLIMIT
```

Newton barrier: The maximum number of iterations. (integer)

While the simplex method usually performs a number of iterations which is proportional to the number of constraints (rows) in a problem, the barrier method standardly finds the optimal solution to a given accuracy after a number of iterations which is independent of the problem size. The penalty is rather that the time for each iteration increases with the size of the problem. `BARITERLIMIT` specifies the maximum number of iterations which will be carried out by the barrier.

Default value: `500`

Domain: 0~+INF
