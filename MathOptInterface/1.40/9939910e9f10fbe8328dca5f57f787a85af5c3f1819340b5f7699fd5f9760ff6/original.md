```
SOLUTION_LIMIT::TerminationStatusCode
```

An instance of the [`TerminationStatusCode`](@ref) enum.

## About

The algorithm stopped because it found the required number of solutions. This is often used in MIPs to get the solver to return the first feasible solution it encounters.

This status may be returned in relation to the [`SolutionLimit`](@ref) attribute, or some other solver-specific attribute.
