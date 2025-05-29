```
XPRS_MULTIOBJOPS
```

Modifies the behaviour of the optimizer when solving multi-objective problems. (integer)

Default value: `7` (all bits are set)

Values are a bitset: bit 0 : `XPRS_MULTIOBJOPS_ENABLED`Multi-objective enabled. If this bit is not set, multi-objective problems will treated as single-objective problems, and only objective `0` will be optimized. bit 1 : `XPRS_MULTIOBJOPS_PRESOLVE`Apply multi-objective modifications during presolve. If this bit is not set, the original problem will be modified when solving each subsequent objective, and these modifications will remain in the problem after the solve has completed. bit 2 : `XPRS_MULTIOBJOPS_RCFIXING`Reduced cost fixing. If this bit is set, optimality of earlier objectives will be preserved by fixing all non-basic variables with non-zero reduced costs to their bounds. If not set, optimality of earlier objectives will be preserved by adding constraints to the problem.
