```
c2d(css::ContinuouStateSpace, h::Float64, method::Symbol)
```

Converts a continuous-time state-space model to a discrete-time state-space model.

**Inputs**

  * `css`: Continuous-time state-space model
  * `h`: Sampling time.
  * `method`: Discretization method

      * `:zoh`: Zero-order Hold method
      * `:foh`: First-order Hold method
      * `:blh`: Band-limited Hold method
      * `:rk4`: 4th order Runge-Kutta method

**Output**

  * `DiscreteStateSpace`: Discrete-time state-space model

      * `Ad`: Discrete-time state-space matrix A
      * `Bd`: Discrete-time state-space matrix B
      * `Bdp`: Discrete-time state-space matrix Bp (only for `:foh` and `:rk4` methods)
