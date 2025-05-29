```
generate_initial_model(; hSets, hData, hParameters)
```

Produces an initial model container based on data, parameters and sets.

### Args:

  * `hSet`: a dictionary of sets
  * `hData`: a dictionary of data
  * `hParameters`: a dictionary of parameters

## Returns:

A model container with the following elements:

  * `model`: an empty Ipopt model
  * `data`: a dictionary of data (variables in the model)
  * `parameters`: a dictionary of parameter values
  * `sets`: a dictionary of sets
  * `fixed`: a dictionary of Boolean arrays defining the closure of the model (exogenous/fixed variables)
  * `lower`: a dictionary of lower bounds for model variables
  * `upper`: a dictionary of upper bounds for model variables

### Example:

$julia generate_initial_model(; hSets, hData, hParameters)$
