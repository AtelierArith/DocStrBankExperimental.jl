```
bijector(T::AbstractParameters [, k::Symbol])
```

Returns the function for the change of variables of the parameters.

The function is a bijection from the supports/domains of the priors to ℝⁿ, from the Bijectors.jl package. You can specify the parameter symbol to get the bijector of that parameter.
