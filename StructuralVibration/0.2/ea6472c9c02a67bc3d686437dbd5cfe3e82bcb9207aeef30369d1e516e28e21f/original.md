```
solve(prob::DirectTimeProblem, alg; progress = true)
```

Direct time integration solver

**Inputs**

  * `prob`: DirectTimeProblem structure
  * `alg`: Numerical integration algorithm

      * `CentralDiff()`: Central difference
      * `RK4()`: Fourth-order Runge-Kutta
      * `Newmark()`: Newmark
      * `HHT()`: Hilber-Hughes-Taylor
      * `WBZ()`: Wood-Bossak-Zienkiewicz
      * `GeneralizedAlpha()`: Generalized-α (default)
      * `MidPoint()`: Mid-point rule
  * `progress`: Show progress bar

**Output**

  * `sol`: Solution structure containing the response of the system at the given time points

      * `u`: Displacement
      * `du`: Velocity
      * `ddu`: Acceleration
