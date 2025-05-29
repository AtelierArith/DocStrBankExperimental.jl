```
cocoPredictKsteps(cocoReg_fit, k, number_simulations=500, covariates=nothing, link="log", matrix_fill=zeros(Int64(number_simulations), Int64(k)))
```

Generates a k-step ahead predictive distribution by simulating the model multiple times.

# Arguments

  * `cocoReg_fit`: A dictionary containing the fitted model details.
  * `k`: The number of steps ahead to predict.
  * `number_simulations` (optional): The number of simulation runs to generate the predictive distribution (default is 500).
  * `covariates` (optional): Optional covariate data to use in the simulations.
  * `link` (optional): A string specifying the link function (default is `"log"`).
  * `matrix_fill` (optional): A preallocated matrix to store simulation results (default is a zeros matrix with dimensions `number_simulations` x `k`).

# Returns

A dictionary where each key `"prediction_i"` contains a DataFrame of count values and their relative frequencies for step `i`. Also includes a key `"length"` indicating the number of prediction steps.
