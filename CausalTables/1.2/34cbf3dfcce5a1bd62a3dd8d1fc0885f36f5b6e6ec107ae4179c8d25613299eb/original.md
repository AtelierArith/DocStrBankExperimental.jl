```
rand(scm::StructuralCausalModel, n::Int)
```

Generate random data from a Structural Causal Model (SCM) using the specified number of samples.

# Arguments

  * `scm::StructuralCausalModel`: The Structural Causal Model from which to generate data.
  * `n::Int`: The number of samples to generate.

# Returns

A `CausalTable` object containing the generated data.
