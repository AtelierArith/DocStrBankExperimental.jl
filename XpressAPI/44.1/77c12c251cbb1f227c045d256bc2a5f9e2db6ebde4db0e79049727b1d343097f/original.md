```
XPRS_MIPRAMPUP
```

Controls the strategy used by the parallel MIP solver during the ramp-up phase of a branch-and-bound tree search. (integer)

Default value: -1

Values: -1 : Automatically determined. 0 : No special treatment during the ramp-up phase. Always run with the maximal number of tasks. 1 : Limit the number of tasks until the initial dives have completed.
