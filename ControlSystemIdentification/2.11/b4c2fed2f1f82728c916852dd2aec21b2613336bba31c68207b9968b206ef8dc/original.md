```
predplot(sys, data, x0=:estimate; ploty=true, plote=false, h=1, sysname="")
```

Plot system `h`-step prediction and measured output to compare them.

By default, the initial condition `x0` is estimated using the data. To start the simulation from the origin, provide `x0 = :zero` or `x0 = zeros(sys.nx)`.

  * `ploty` determines whether or not to plot the measured signal
  * `plote` determines whether or not to plot the residual
  * `h` is the prediction horizon.
