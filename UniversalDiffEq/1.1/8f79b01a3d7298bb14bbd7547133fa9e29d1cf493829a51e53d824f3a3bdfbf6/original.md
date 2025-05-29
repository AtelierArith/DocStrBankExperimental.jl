```
CustomModel(data::DataFrame,X::DataFrame, derivs!::Function, initial_parameters; kwargs ...)
```

Constructs a UDE model from a DataFrame `data` a DataFrame with covariates `X` a function `derivs` and an initial guess of the paramter values `inital_parameters`. The modle strucutre can be further modified by the key word arguments to specify the relationship between the state variables and observations and the loss function.  These areguments are discussed individuals below. 

# kwargs

link - A function that takes the value of the state variable `u` and paramters `p` and retuns and estiamte of the obseration `y` link*params - parameters for the link function, can be an empty NamedTuple if no paramters are used observation*loss - loss function that describes the distance betwen the observed and estimated states observation*params - parameters for the obseraiton loss function - can be an empty named tuple of no paramters are needed process*loss - loss funciton that describes the distance betwen the observed and predicted state tranistions.  process*loss*params - parameters for the process loss.  state*variable*transform - a function that maps from the variables used in the optimizer to states variables used by the observaiton and prediction funitons.  log*priors - prior probabilities for the model paramters + nerual network regularization  time*column*name - column that indexes time in the data frames value*column*name - the column that indicates the variabe in  long formate covariates data sets  variable*column*name = the column that indicates the value of the variables in long formate covariates data sets  reg*weight -  weight given to regualrizing the neural network  reg_type - funcrional form of regualrization "L1" or "L2"
