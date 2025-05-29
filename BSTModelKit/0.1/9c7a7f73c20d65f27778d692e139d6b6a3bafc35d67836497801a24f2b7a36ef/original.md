```
morris(performance::Function, L::Array{Float64,1}, U::Array{Float64,1}; 
    number_of_samples::Int64 = 1000) -> Array{Float64,2}
```

The `morris` function is a wrapper around the `gsa` function that uses the Morris method to perform a global sensitivity analysis.

### Arguments

  * `performance::Function`: a function that takes a vector of parameters and returns a scalar performance metric.
  * `L::Array{Float64,1}`: a vector of lower bounds for the parameters.
  * `U::Array{Float64,1}`: a vector of upper bounds for the parameters.
  * `number_of_samples::Int64`: the number of samples to use in the analysis.

### Returns

  * a matrix of results where the first column is the mean and the second column is the variance of the sensitivity analysis.
