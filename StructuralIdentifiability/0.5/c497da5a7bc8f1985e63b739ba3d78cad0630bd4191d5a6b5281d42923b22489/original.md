```
assess_identifiability(ode; funcs_to_check = [], prob_threshold=0.99, loglevel=Logging.Info)
```

Input:

  * `ode` - the ODE model
  * `funcs_to_check` - list of functions to check identifiability for; if empty, all parameters  and states are taken
  * `known_ic`: a list of functions whose initial conditions are assumed to be known, then the returned identifiable functions will be functions of parameters and initial conditions, not states (this is an experimental functionality).
  * `prob_threshold` - probability of correctness.
  * `loglevel` - the minimal level of log messages to display (`Logging.Info` by default)

Assesses identifiability of a given ODE model. The result is guaranteed to be correct with the probability at least `prob_threshold`. The function returns an (ordered) dictionary from the functions to check to their identifiability properties  (one of `:nonidentifiable`, `:locally`, `:globally`).
