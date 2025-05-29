```
RungeKutta(order=4; supersample=1)
```

Create an explicit Runge-Kutta solver with optional super-sampling.

The argument `order` specifies the order of the Runge-Kutta solver, which must be 1 or 4. The keyword argument `supersample` provides the number of internal steps (default to 1 step). This solver is allocation-free if the `f!` and `h!` functions do not allocate.
