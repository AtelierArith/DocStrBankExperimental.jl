```
XPRS_DUALSTRATEGY
```

This bit-vector control specifies the dual simplex strategy. (integer)

Default value: `1`

Values are a bitset: bit 0 : Switch to primal when re-optimization goes dual infeasible and numerically unstable. bit 1 : When dual intend to switch to primal, stop the solve instead of switching to primal. bit 2 : Use more aggressive cut-off in MIP search. bit 3 : Use dual simplex to remove cost perturbations. bit 4 : Enable more aggressive dual pivoting strategy. bit 5 : Keep using dual simplex even when it's numerically unstable.
