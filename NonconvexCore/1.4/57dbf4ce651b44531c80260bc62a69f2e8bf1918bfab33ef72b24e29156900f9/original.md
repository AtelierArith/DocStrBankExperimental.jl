```
ScaledKKTCriteria
```

This convergence criteria uses another scaled version of the Karush-Kuhn-Tucker (KKT) residual and maximum infeasibility to assess convergence. In particular if the objective was scaled by a factor `m`, the KKT residual will be scaled down by a factor `max(m, 1/m)`. This scaling was found to make the convergence criteria less sensitive to scale compared to using the traditional KKT residual. More details are given in [`assess_convergence!`](@ref). 
