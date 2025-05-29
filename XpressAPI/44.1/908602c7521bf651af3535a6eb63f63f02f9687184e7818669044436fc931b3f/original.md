```
XPRS_BARGAPTARGET
```

Newton barrier: The target tolerance for the relative duality gap. (double)

The barrier algorithm will keep iterating until either `BARGAPTARGET` is satisfied or until no further improvements are possible. In the latter case, if BARGAPSTOP is satisfied, it will declare the problem optimal.

Default value: `0`

Values: 0 : The default value is determined automatically based on the problem size, structure and algorithm choice.

> =0


: The target tolerance for the relative duality gap.
