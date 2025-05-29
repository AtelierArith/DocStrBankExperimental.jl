```
generate_starting_values(; hSets, hData, hParameters)
```

Produces starting values for all required variables in the model. This is typically not called by the user; instead, this is invoked in the process of producing the initial model.

### Args:

  * `hSets`: a dictionary of sets
  * `hData`: a dictionary of data
  * `hParameters`: a dictionary of parameters

### Returns:

A named tuple with six elements: sets `sets`, parameters `parameters`, data `data`, closure `fixed`, lower bounds `lower`, and upper bounds `upper`
