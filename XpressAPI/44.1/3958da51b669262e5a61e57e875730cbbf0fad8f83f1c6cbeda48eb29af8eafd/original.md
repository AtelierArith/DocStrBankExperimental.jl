```
XPRS_CLAMPING
```

This control allows for the adjustment of returned solution values such that they are always within bounds. (integer)

Default value: `0`

Values are a bitset: bit -1 : Determined automatically. bit 0 : Adjust primal solution to always be within primal bounds. Slacks if provided will be adjusted accordingly. bit 1 : Adjust primal slack values to always be within constraint bounds. bit 2 : Adjust dual solution to always be within the dual bounds implied by the slacks. Reduced costs, if provided, will be adjusted accordingly. bit 3 : Adjust reduced costs to always be within dual bounds implied by the primal solution.
