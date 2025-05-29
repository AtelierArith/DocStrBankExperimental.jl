```
NumParams(tf::Float64,dt::Float64,scheme::String,st::Int,tol::Float64)
```

Numerical parameters needed for the time marching scheme.

## Fields

  * `tf`: The end time of this run
  * `dt`: Time step size
  * `scheme`: Applies the implicit Runge-kutta method of different coefficient, choices   are "Liska"(2nd order), "BH3"(3rd order), "BH5"(4th order), "Euler"(1st order),   "RK2"(2nd order), "RK22"(2nd order).
  * `st`: The number of stages of this RK scheme
  * `tol`: Tolerance used in time marching for adptive time step
