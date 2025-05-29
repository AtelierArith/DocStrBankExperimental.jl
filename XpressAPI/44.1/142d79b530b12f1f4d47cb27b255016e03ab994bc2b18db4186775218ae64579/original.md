```
XPRS_PWLDUALREDUCTIONS
```

This parameter specifies whether dual reductions should be applied to reduce the number of columns, rows and SOS-constraints added when transforming piecewise linear objectives and constraints to MIP structs. (integer)

Default value: `1`

Values: 0 : Disabled. No dual reductions, add all columns, rows and SOS-constraints. 1 : Enabled. Only add neccessary columns, rows and sets, drop those implied by the objective sense.
