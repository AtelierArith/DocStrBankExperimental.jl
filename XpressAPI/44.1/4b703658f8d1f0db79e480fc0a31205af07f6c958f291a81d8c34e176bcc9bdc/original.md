```
XPRS_KEEPBASIS
```

Simplex: This determines whether the basis should be kept when reoptimizing a problem. (integer)

The choice is between using a crash basis created at the beginning of simplex or using a basis from a previous solve (if such exists). By default, this control gets (re)set automatically in various situations. By default, it will be automatically set to 1 after a solve that produced a valid basis. This will automatically warmstart a subsequent solve. Explicitly loading a starting basis will also set this control to 1. If the control is explicitly set to 0, any existing basis will be ignored for a new solve, and the Optimizer will start from an ad-hoc crash basis.

Default value: `0`

Values: 0 : Problem optimization starts from scratch, i.e., any previous basis is ignored. 1 : The previous basis should be used as a starting basis. 2 : Use the previous basis only if it is valid for the current problem (the number of basic variables must match the number of rows). 3 : Use the previous basis only if it is valid and numerically stable in the current problem.
