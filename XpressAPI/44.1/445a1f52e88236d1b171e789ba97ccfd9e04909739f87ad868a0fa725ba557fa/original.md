```
XPRS_HEURSHIFTPROP
```

Determines whether the Shift-and-propagate primal heuristic should be executed. (integer)

If enabled, Shift-and-propagate is an LP-free primal heuristic that is executed immediately after presolve.

Default value: `-1`

Values: -1 : The solver decides if Shift-and-propagate should be run. This is the default setting. 0 : Shift-and-propagate is disabled. 1 : Shift-and-propagate is enabled.
