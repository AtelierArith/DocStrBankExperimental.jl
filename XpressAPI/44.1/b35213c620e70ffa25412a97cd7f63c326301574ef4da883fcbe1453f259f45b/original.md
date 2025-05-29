```
XPRS_GENCONSDUALREDUCTIONS
```

This parameter specifies whether dual reductions should be applied to reduce the number of columns and rows added when transforming general constraints to MIP structs. (integer)

Default value: `1`

Values: 0 : Disabled. No dual reductions, add columns and rows. 1 : Enabled. Only add neccessary columns and rows, drop those implied by the objective sense.
