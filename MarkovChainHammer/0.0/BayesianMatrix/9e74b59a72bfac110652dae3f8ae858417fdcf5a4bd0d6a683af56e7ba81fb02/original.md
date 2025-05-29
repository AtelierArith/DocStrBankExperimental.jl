```
BayesianGenerator(data, prior::GeneratorParameterDistributions; dt=1)
```

Construct a BayesianGenerator object from data and a prior distribution.

# Arguments

  * `data::Vector{Int}`: The data to construct the BayesianGenerator object from.
  * `prior::GeneratorParameterDistributions`: The prior distribution for the BayesianGenerator object.

# Keyword Arguments

  * `dt::Number=1`: The time step between each data point.

# Returns

  * `BayesianGenerator`: A BayesianGenerator object constructed from the data and the prior distribution. Contains the posterior distributions for the rates and exit probabilities, as well as the predictive distributions for the holding times and exit counts.
