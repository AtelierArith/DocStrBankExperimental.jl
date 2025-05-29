```
XPRS_BARSTEPSTOP
```

Newton barrier: A convergence parameter, representing the minimal step size. (double)

On each iteration of the barrier algorithm, a step is taken along a computed search direction. If that step size is smaller than `BARSTEPSTOP`, the Optimizer will terminate and return the current solution.

Default value: `1.0E-16`

Domain: [-INF,+INF]
