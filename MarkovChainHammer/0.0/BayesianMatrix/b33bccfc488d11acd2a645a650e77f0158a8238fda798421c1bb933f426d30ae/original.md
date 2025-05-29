```
uninformative_prior(number_of_states; scale=eps(1e2))
```

Construct an uninformative prior distribution for a BayesianGenerator object.

# Arguments

  * `number_of_states::Int`: The number of states in the BayesianGenerator object.

# Keyword Arguments

  * `scale::Number=eps(1e2)`: The scale parameter for the Gamma and Dirichlet distributions.

# Returns

  * `GeneratorParameterDistributions`: An uninformative prior distribution for a BayesianGenerator object.
