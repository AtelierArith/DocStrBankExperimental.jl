```
build_model!(mc; max_iter=50, constr_viol_tol=1e-8, bound_push=1e-15)
```

Builds the GTAP model in the provided model container (`mc`) which has an empty Ipopt model. This function is not typically called by the user; instead, it is invoked by `generate_initial_model()`. However, if the user wishes to change the model, he or she can extend this function.

### Args:

  * `mc`: a model container

### Optional args:

  * `max_iter`: maximum number of iterations
  * `constr_viol_tol`: accuracy for constraint satisfaction
  * `bound_push`: mandatory move of the starting values from constraint bounds

### Retruns:

Nothing but it modifies the `mc` object, adding on the existing `model` element

### Example:

`julia build_model!(mc)`
