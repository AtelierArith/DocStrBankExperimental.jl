```
XPRS_BARDUALSTOP
```

Newton barrier and hybrid gradient: This is a convergence parameter, representing the tolerance for dual infeasibilities. (double)

If the difference between the constraints and their bounds in the dual problem falls below this tolerance in absolute value, optimization will stop and the current solution will be returned.

Default value: `0`

Values: 0 : The default value is determined automatically based on the problem size, structure and algorithm choice.

> =0


: The tolerance for dual infeasibilities.
