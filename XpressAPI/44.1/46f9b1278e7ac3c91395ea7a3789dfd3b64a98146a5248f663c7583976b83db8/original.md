```
XPRS_OBJSCALEFACTOR
```

Custom objective scaling factor, expressed as a power of 2. (double)

When set, it overwrites the automatic objective scaling factor. A value of 0 means no objective scaling. This control is applied for the full solve, and is independent of any extra scaling that may occur specifically for the barrier or simplex solvers. As it is a power of 2, to scale by 16, set the value of the control to 4.

Default value: `0`

Domain: (-64, +64]
