```
condensity(scm::StructuralCausalModel, ct::CausalTable, name::Symbol)
```

Compute the conditional density of variable `name` in CausalTable `ct` that has been drawn from StructuralCausalModel `scm`.

# Arguments

  * `scm::StructuralCausalModel`: The StructuralCausalModel representing the data generating process.
  * `ct::CausalTable`: The CausalTable containing the observed data.
  * `name::Symbol`: The variable for which to compute the conditional density.

# Returns

The conditional density of the variable `var` given the observed data.
