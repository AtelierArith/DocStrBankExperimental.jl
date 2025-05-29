```
sssolve!(model; <options>)
```

Solve the steady state problem for the given model.

### Options

Standard options (default values are taken from `model.options`)

  * `verbose`
  * `tol`, `maxiter` - control the stopping criteria of the solver

Specific options

  * `presolve::Bool` - whether or not to use a presolve pass. Default is `true`.
  * `method::Symbol` - choose the solution algorithm. Valid options are `:nr` for Newton-Raphson, `:lm` for Levenberg-Marquardt, and `:auto`. The `:auto` method starts with the LM algorithm and automatically switches to NR when it starts to converge. Default is `:nr`.
