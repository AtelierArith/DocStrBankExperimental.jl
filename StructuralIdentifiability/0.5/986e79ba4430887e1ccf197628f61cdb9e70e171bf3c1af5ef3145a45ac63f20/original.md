```
find_ioequations(ode, [var_change_policy=:default])
```

Finds the input-output equations of an ODE system Input:

  * `ode` - the ODE system
  * `var_change_policy` - whether to perform automatic variable change, can be one of `:default`, `:yes`, `:no`
  * `loglevel` - logging level (default: Logging.Info)

Output:

  * a dictionary from “leaders” to the corresponding input-output equations; if an extra projection is needed, it will be the value corresponding to `rand_proj_var`
