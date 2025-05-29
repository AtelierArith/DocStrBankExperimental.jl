```
BayesianGenerator(parameters::NamedTuple)
```

Construct a BayesianGenerator object from a NamedTuple of parameters.

# Arguments

  * `parameters::NamedTuple`: A NamedTuple containing the parameters for the BayesianGenerator object. Must contain the fields `prior`, `posterior` and `predictive`, each of which must be a NamedTuple containing the parameters for the respective distributions.

# Returns

  * `BayesianGenerator`: A BayesianGenerator object constructed from the parameters. Contains the posterior distributions for the rates and exit probabilities, as well as the predictive distributions for the holding times and exit counts.
