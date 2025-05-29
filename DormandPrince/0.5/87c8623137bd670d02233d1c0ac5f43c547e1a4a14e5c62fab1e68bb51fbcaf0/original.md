```
struct DP5Solver
```

A 5th Order Dormand-Prince solver object that contains:

  * the ODE problem of interest
  * The solution to the ODE at the last integrated-to time point
  * intermediate arrays used in the Runge-Kutta method
  * constants and variables used by the solver
  * user-provided options for the solver

The storage of such intermediate information allows for efficient integration from a previously integrated-to  time point and a future time point.
