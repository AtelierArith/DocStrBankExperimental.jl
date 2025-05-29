```
propensity(scm::StructuralCausalModel, ct::CausalTable, name::Symbol)
```

Compute the (generalized) propensity score of variable `name` in CausalTable `ct` that has been drawn from StructuralCausalModel `scm`.

# Arguments

  * `scm::StructuralCausalModel`: The StructuralCausalModel object representing the data generating process.
  * `ct::CausalTable`: The CausalTable object representing the data.
  * `name::Symbol`: The variable for which to compute the conditional mean.

# Returns

An array of conditional probabilities for the specified variable (or densities, if the specified variable is continuous).
