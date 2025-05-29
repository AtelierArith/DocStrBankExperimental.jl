```
set_approximation_mode(m::GMPModel, mode::AbstractApproximationMode)
```

Set the approximation mode of m to mode. Depending on the solver either the primal or the dual formulation might be more efficient. It might also be interesting to change the mode when numerical issues are encountered. Possible values for mode are:

  * PRIMAL*RELAXATION*MODE()
  * DUAL*STRENGTHEN*MODE() (default)

```

```
