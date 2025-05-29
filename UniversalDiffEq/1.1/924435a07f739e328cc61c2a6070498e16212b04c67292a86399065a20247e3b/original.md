```
UDE
```

Basic data structure used to the model structure, parameters and data for UDE and NODE models. ...

# Elements

  * times: a vector of times for each observation
  * data: a matrix of observations at each time point
  * X: a DataFrame with any covariates used by the model
  * data_frame: a DataFrame with columns for the time of each observation and values of the state variables
  * parameters: a ComponentArray that stores model parameters
  * loss_function: the loss function used to fit the model
  * process_model: a Julia mutable struct used to define model predictions
  * process_loss: a Julia mutable struct used to measure the performance of model predictions
  * observation_model: a Julia mutable struct used to predict observations given state variable estimates
  * observation_loss: a Julia mutable struct used to measure the performance of the observation model
  * process_regularization: a Julia mutable struct used to store data needed for process model regularization
  * observation_regularization: a Julia mutable struct used to store data needed for observation model regularization
  * constructor: A function that initializes a UDE model with identical structure.
  * time*column*name: A string with the name of the column used for
  * weights
  * variable*column*name
  * value*column*name

...
