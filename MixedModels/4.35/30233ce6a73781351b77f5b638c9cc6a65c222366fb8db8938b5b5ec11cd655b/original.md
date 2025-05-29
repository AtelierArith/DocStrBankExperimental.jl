```
OptSummary
```

Summary of an optimization

# Fields

## Tolerances, initial and final values

  * `initial`: a copy of the initial parameter values in the optimization
  * `finitial`: the initial value of the objective
  * `lowerbd`: lower bounds on the parameter values
  * `final`: a copy of the final parameter values from the optimization
  * `fmin`: the final value of the objective
  * `feval`: the number of function evaluations  Available backends can be examined via `OPTIMIZATION_BACKENDS`.
  * `returnvalue`: the return value, as a `Symbol`. The available return values will differ between backends.
  * `xtol_zero_abs`: the tolerance for a near zero parameter to be considered practically zero
  * `ftol_zero_abs`: the tolerance for change in the objective for setting a near zero parameter to zero
  * `maxfeval`: as in NLopt (`maxeval`) and PRIMA (`maxfun`)

## Choice of optimizer and backend

  * `optimizer`: the name of the optimizer used, as a `Symbol`
  * `backend`: the optimization library providing the optimizer, default is `NLoptBackend`.

## Backend-specific fields

  * `ftol_rel`: as in NLopt, not used in PRIMA
  * `ftol_abs`: as in NLopt, not used in PRIMA
  * `xtol_rel`: as in NLopt, not used in PRIMA
  * `xtol_abs`: as in NLopt, not used in PRIMA
  * `initial_step`: as in NLopt, not used in PRIMA
  * `maxtime`: as in NLopt, not used in PRIMA
  * `rhobeg`: as in PRIMA, not used in NLopt
  * `rhoend`: as in PRIMA, not used in NLopt

## MixedModels-specific fields, unrelated to the optimizer

  * `fitlog`: A vector of tuples of parameter and objectives values from steps in the optimization
  * `nAGQ`: number of adaptive Gauss-Hermite quadrature points in deviance evaluation for GLMMs
  * `REML`: use the REML criterion for LMM fits
  * `sigma`: a priori value for the residual standard deviation for LMM

!!! note
    The internal storage of the parameter values within `fitlog` may change in the future to use a different subtype of `AbstractVector` (e.g., `StaticArrays.SVector`) for each snapshot without being considered a breaking change.


!!! note
    The exact order and number of fields may change as support for additional backends and features thereof are added. In other words: use the keyword constructor and do **not** use the positional constructor.

