```
termination_forwards(vₑ, [quiet])
```

Construct termination criteria of solving PN evolution forwards in time

These criteria include checking that the masses are positive and the dimensionless spins are less than 1, as well as ensuring that the evolution will terminate at `vₑ`.

The optional `quiet` argument will silence informational messages about reaching the target value of `vₑ` if set to `true`, but warnings will still be issued when terminating for other reasons.
