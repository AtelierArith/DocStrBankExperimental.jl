```
run_model!(model_container; max_iter=50, constr_viol_tol=1e-8, bound_push=1e-15)
```

Runs the model (model*container.model) by executing these steps: (1) set all starting  values to those found in the data (model*container.data), (2) fix all variables that are specified as exogenous (model*container.fixed), (3) solve the model, (4) load all variable values to the data (model*container.data)

### Args:

  * `model_container`: model container

### Optional args:

  * `max_iter`: maximum number of iterations
  * `constr_viol_tol`: accuracy for constraint satisfaction
  * `bound_push`: mandatory move of the starting values from constraint bounds
