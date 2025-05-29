```
XPRS_BARPRIMALSTOP
```

Newton barrier and hybrid gradient: This is a convergence parameter, indicating the tolerance for primal infeasibilities. (double)

If the difference between the constraints and their bounds in the primal problem falls below this tolerance in absolute value, the Optimizer will terminate and return the current solution.

Default value: `0`

Values: 0 : The default value is determined automatically based on the problem size, structure and algorithm choice.

> =0


: The tolerance for primal infeasibilities.
