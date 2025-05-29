```
get_params(model, turing_param)
```

For a given `model` and a *single* pattern-forming parameter set, `turing_param`, this function creates a  corresponding `model_parameters` variable. This sets, by default, the `model_parameters` fields:

  * `domain_size`: chosen to be 3x the computed pattern wavelength, i.e., `3*turing_param.wavelength`
  * `initial_condition`: chosen to be the computed steady state values, i.e.,  `turing_param.steady_state_values`
  * `initial_noise = 0.01`: the magnitude of noise (normally distributed random numbers) added to the steady state values to define the initial conditions.
