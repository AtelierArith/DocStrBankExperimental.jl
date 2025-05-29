```
Highs_addVars(highs, num_new_var, lower, upper)
```

Add multiple variables to the model.

### Parameters

  * `highs`: A pointer to the Highs instance.
  * `num_new_var`: The number of new variables to add.
  * `lower`: An array of size [num_new_var] with lower bounds.
  * `upper`: An array of size [num_new_var] with upper bounds.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
