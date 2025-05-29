```
Estimation
Estimation(model,toestimate,filepaths,ignorefield,objective_form)
```

## Input parameters:

  * `model`: The initial model containing the species we wish to parameterise
  * `toestimate`: The dictionary of parameters being fitted
  * `filepaths` or `filepaths_weights`: The location of the data files used to fit. Can also contain the weights of each dataset
  * `ignorefield`: Specify which EoSModel fields to ignore in the main model
  * `objective_form`: Specify the functional form of the objective function in the form `objective_form(pred,exp)`

## Output:

Estimator object which contains the following:

  * `model`: The model whose parameters will be varied
  * `initial_model`: The initial model before parameterisation
  * `toestimate`: ToEstimate struct which contains all the information on the parameters
  * `data`: Vector of `EstimationData` structs where all the information on the data is stored
  * `ignorefield`: Vector of fields to ignore in the parameter estimation
  * `objective_form`: Function to evaluate the error measure for the objective function

The following objects are also output:

  * `objective`: The objective function which is used to fit the parameters
  * `x0`: Initial guesses for the parameters
  * `upper`: Upper bounds for the parameters
  * `lower`: Lower bounds for the parameters

## Description

Produces the estimator and other useful objects used within parameter estimation
