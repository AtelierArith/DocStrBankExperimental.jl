```
model_psd_variables_as_free_variables!(problem::Problem, as_free)
```

Model the positive semidefinite variables with names in `as_free` using free variables,  and add extra constraints to set them equal to auxilliary positive semidefinite variables.
