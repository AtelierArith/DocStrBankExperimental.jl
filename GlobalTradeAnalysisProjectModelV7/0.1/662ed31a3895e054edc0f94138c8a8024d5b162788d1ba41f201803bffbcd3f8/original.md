```
    calculate_expenditure(; sets, data0, data1, parameters, max_iter=50, constr_viol_tol=1e-5, bound_push=1e-15)
```

Calculate the expenditure at post simulation utility (in data1) at original prices (data0)

### Args:

  * `sets`: a dictionary of sets
  * `data0`: a dictionary of data from baseline solution
  * `data1`: a dictionary of data from simulation solution
  * `parameters`: a dictionary of parameters

### Optional args:

  * `max_iter`: maximum number of iterations
  * `constr_viol_tol`: accuracy for constraint satisfaction
  * `bound_push`: mandatory move of the starting values from constraint bounds

### Returns:

A vector of expenditures.
